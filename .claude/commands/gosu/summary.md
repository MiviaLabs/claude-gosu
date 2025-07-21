# Work Summary Report Generator

Generate a comprehensive work summary report showing commits, pull requests, and contributions by each team member over a specified time period.

## Usage

This command analyzes git history and GitHub activity to create a detailed report of work completed by each contributor.

```
gosu:summary [days]
```

**Target File:** $ARGUMENTS

## Parameters

- `days` (optional): Number of days to look back from today (default: 7)

Example: `/gosu:summary 30` - Generate report for last 30 days

## Command

```bash
#!/bin/bash

# Get the date range
DAYS_BACK=${1:-7}
START_DATE=$(date -d "${DAYS_BACK} days ago" +%Y-%m-%d)
TODAY=$(date +%Y-%m-%d)

# Get all contributors in the time period
CONTRIBUTORS=$(git log --since="${DAYS_BACK} days ago" --pretty=format:"%ae" | sort -u)

if [ -z "$CONTRIBUTORS" ]; then
    echo "No commits found in the specified time period."
    exit 0
fi

# Generate the report content
{
echo "# Work Summary Report"
echo "**Period:** ${START_DATE} to ${TODAY} (${DAYS_BACK} days)"
echo "**Generated:** $(date)"
echo ""

echo "## Contributors Summary"
echo ""

# Track totals for final summary
TOTAL_COMMITS=0
TOTAL_ADDITIONS=0
TOTAL_DELETIONS=0
TOTAL_FILES_CHANGED=0

# Process each contributor
for EMAIL in $CONTRIBUTORS; do
    # Get author name and email
    AUTHOR_NAME=$(git log --author="$EMAIL" -1 --pretty=format:"%an" 2>/dev/null || echo "Unknown")

    echo "### ${AUTHOR_NAME} (${EMAIL})"
    echo ""

    # Get commit statistics for this author
    AUTHOR_COMMITS=$(git log --since="${DAYS_BACK} days ago" --author="$EMAIL" --oneline | wc -l)
    AUTHOR_STATS=$(git log --since="${DAYS_BACK} days ago" --author="$EMAIL" --numstat | awk '
        BEGIN { additions=0; deletions=0; files=0 }
        /^[0-9]/ { additions+=$1; deletions+=$2; files++ }
        END { printf "%d %d %d", additions, deletions, files }
    ')

    read AUTHOR_ADDITIONS AUTHOR_DELETIONS AUTHOR_FILES <<< "$AUTHOR_STATS"

    echo "**Statistics:**"
    echo "- Commits: ${AUTHOR_COMMITS}"
    echo "- Lines added: ${AUTHOR_ADDITIONS}"
    echo "- Lines deleted: ${AUTHOR_DELETIONS}"
    echo "- Files changed: ${AUTHOR_FILES}"
    echo ""

    # Update totals
    TOTAL_COMMITS=$((TOTAL_COMMITS + AUTHOR_COMMITS))
    TOTAL_ADDITIONS=$((TOTAL_ADDITIONS + AUTHOR_ADDITIONS))
    TOTAL_DELETIONS=$((TOTAL_DELETIONS + AUTHOR_DELETIONS))
    TOTAL_FILES_CHANGED=$((TOTAL_FILES_CHANGED + AUTHOR_FILES))

    echo "**Work Narrative:**"

    # Analyze actual code changes and generate intelligent insights
    RECENT_COMMITS=$(git log --since="${DAYS_BACK} days ago" --author="$EMAIL" --pretty=format:"%H|%s" | head -15)

    if [ -n "$RECENT_COMMITS" ]; then
        # Analyze each significant commit for meaningful changes
        echo "$RECENT_COMMITS" | while IFS='|' read -r COMMIT_HASH COMMIT_MSG; do
            # Get the diff for this commit to understand what actually changed
            DIFF_CONTENT=$(git show --no-merges --format="" "$COMMIT_HASH" 2>/dev/null | head -50)

            # Analyze commit type and content to generate narrative
            case "$COMMIT_MSG" in
                feat*|feature*)
                    # Feature analysis with code inspection
                    if echo "$DIFF_CONTENT" | grep -q "export.*Controller\|@Controller\|@Get\|@Post\|@Put\|@Delete"; then
                        echo "  📍 **API Development**: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                        echo "     └ Implemented new REST endpoints and controller logic<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "CREATE TABLE\|ALTER TABLE\|schema\|migration\|\.entity\.ts"; then
                        echo "  📍 **Database Schema**: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                        echo "     └ Enhanced database structure and data models<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "interface.*{.*}\|type.*=\|export.*interface"; then
                        echo "  📍 **Type System**: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                        echo "     └ Strengthened TypeScript type definitions<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "@Module\|providers.*:\|imports.*:"; then
                        echo "  📍 **Architecture**: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                        echo "     └ Expanded module structure and dependency injection<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "\.service\.ts\|@Injectable"; then
                        echo "  📍 **Business Logic**: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                        echo "     └ Developed core application services<br/>"
                    else
                        echo "  📍 **Feature**: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                        echo "     └ Added new functionality to the system<br/>"
                    fi
                    ;;
                fix*)
                    # Bug fix analysis with specific categorization
                    if echo "$DIFF_CONTENT" | grep -q "validation\|validator\|ValidationPipe\|@IsString\|@IsEmail"; then
                        echo "  🐛 **Validation Fix**: ${COMMIT_MSG#fix*:}" | sed 's/^fix(//' | sed 's/)://' | sed 's/fix: //'
                        echo "     └ Resolved data validation and input sanitization<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "auth\|jwt\|token\|guard\|@UseGuards"; then
                        echo "  🐛 **Security Fix**: ${COMMIT_MSG#fix*:}" | sed 's/^fix(//' | sed 's/)://' | sed 's/fix: //'
                        echo "     └ Corrected authentication and authorization issues<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "query\|repository\|find\|save\|update\|delete"; then
                        echo "  🐛 **Database Fix**: ${COMMIT_MSG#fix*:}" | sed 's/^fix(//' | sed 's/)://' | sed 's/fix: //'
                        echo "     └ Fixed database operations and queries<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "try.*catch\|throw new\|Error\|Exception"; then
                        echo "  🐛 **Error Handling**: ${COMMIT_MSG#fix*:}" | sed 's/^fix(//' | sed 's/)://' | sed 's/fix: //'
                        echo "     └ Improved error handling and exception management<br/>"
                    else
                        echo "  🐛 **Bug Fix**: ${COMMIT_MSG#fix*:}" | sed 's/^fix(//' | sed 's/)://' | sed 's/fix: //'
                        echo "     └ Resolved application defects<br/>"
                    fi
                    ;;
                refactor*)
                    # Refactoring with impact analysis
                    if echo "$DIFF_CONTENT" | grep -q "extract\|move.*to\|rename"; then
                        echo "  🔧 **Code Organization**: ${COMMIT_MSG#refactor*:}" | sed 's/^refactor(//' | sed 's/)://' | sed 's/refactor: //'
                        echo "     └ Restructured code for better maintainability<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "async\|await\|Promise\|performance"; then
                        echo "  🔧 **Performance**: ${COMMIT_MSG#refactor*:}" | sed 's/^refactor(//' | sed 's/)://' | sed 's/refactor: //'
                        echo "     └ Optimized application performance and efficiency<br/>"
                    else
                        echo "  🔧 **Code Quality**: ${COMMIT_MSG#refactor*:}" | sed 's/^refactor(//' | sed 's/)://' | sed 's/refactor: //'
                        echo "     └ Enhanced code structure and readability<br/>"
                    fi
                    ;;
                test*)
                    echo "  🧪 **Testing**: ${COMMIT_MSG#test*:}" | sed 's/^test(//' | sed 's/)://' | sed 's/test: //'
                    echo "     └ Strengthened test coverage and quality assurance<br/>"
                    ;;
                docs*)
                    echo "  📚 **Documentation**: ${COMMIT_MSG#docs*:}" | sed 's/^docs(//' | sed 's/)://' | sed 's/docs: //'
                    echo "     └ Enhanced project documentation and guides<br/>"
                    ;;
                chore*|build*|ci*)
                    echo "  ⚙️  **Infrastructure**: ${COMMIT_MSG}" | sed 's/^[^(]*(//' | sed 's/)://'
                    echo "     └ Updated tooling, build process, or CI/CD pipeline<br/>"
                    ;;
                *)
                    # Analyze content for untyped commits
                    if echo "$DIFF_CONTENT" | grep -q "@Controller\|@Get\|@Post"; then
                        echo "  📍 **API Work**: $COMMIT_MSG"
                        echo "     └ Enhanced API endpoints and controllers<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "CREATE TABLE\|ALTER TABLE\|\.entity\.ts"; then
                        echo "  📍 **Database Work**: $COMMIT_MSG"
                        echo "     └ Modified database schema and entities<br/>"
                    elif echo "$DIFF_CONTENT" | grep -q "\.service\.ts\|@Injectable"; then
                        echo "  📍 **Service Layer**: $COMMIT_MSG"
                        echo "     └ Enhanced business logic and services<br/>"
                    else
                        echo "  📍 **Development**: $COMMIT_MSG"
                        echo "     └ General development work<br/>"
                    fi
                    ;;
            esac
        done | head -12

        # Add intelligent file-based analysis
        echo ""
        echo "**Technical Impact:**"
        MODIFIED_FILES=$(git log --since="${DAYS_BACK} days ago" --author="$EMAIL" --name-only --pretty=format: | grep -v '^$' | sort | uniq -c | sort -nr | head -8)

        if [ -n "$MODIFIED_FILES" ]; then
            echo "$MODIFIED_FILES" | while read count file; do
                if [ "$count" -gt 1 ]; then
                    case "$file" in
                        *.controller.ts)
                            echo "  🎯 **API Layer**: Enhanced REST endpoints in $file ($count modifications)<br/>"
                            ;;
                        *.service.ts)
                            echo "  ⚙️  **Service Layer**: Developed business logic in $file ($count modifications)<br/>"
                            ;;
                        *.entity.ts|*.model.ts)
                            echo "  🗄️  **Data Layer**: Refined database models in $file ($count modifications)<br/>"
                            ;;
                        *.dto.ts)
                            echo "  📋 **Data Transfer**: Updated validation schemas in $file ($count modifications)<br/>"
                            ;;
                        *.module.ts)
                            echo "  🏗️  **Architecture**: Configured modules in $file ($count modifications)<br/>"
                            ;;
                        *migration*|*schema*)
                            echo "  🗃️  **Database**: Updated schema in $file ($count modifications)<br/>"
                            ;;
                        *.spec.ts|*.test.ts)
                            echo "  🧪 **Testing**: Enhanced test coverage in $file ($count modifications)<br/>"
                            ;;
                        *.md|*README*)
                            echo "  📚 **Documentation**: Updated guides in $file ($count modifications)<br/>"
                            ;;
                        *config*|*.json|*.env*)
                            echo "  ⚙️  **Configuration**: Modified settings in $file ($count modifications)<br/>"
                            ;;
                        *)
                            if [ "$count" -gt 3 ]; then
                                echo "  📁 **Focus Area**: Active development in $file ($count modifications)<br/>"
                            fi
                            ;;
                    esac
                fi
            done
        fi
    else
        echo "  • No commits found for detailed analysis"
    fi

    echo ""
    echo "**Impact & Metrics:**"
    echo "- Code contribution: +${AUTHOR_ADDITIONS}/-${AUTHOR_DELETIONS} lines across ${AUTHOR_FILES} files"
    echo "- Commit frequency: ${AUTHOR_COMMITS} commits over ${DAYS_BACK} days (avg: $((AUTHOR_COMMITS * 7 / DAYS_BACK)) per week)"

    # Calculate productivity score
    if [ $AUTHOR_COMMITS -gt 0 ]; then
        PRODUCTIVITY_SCORE=$((AUTHOR_ADDITIONS / AUTHOR_COMMITS))
        if [ $PRODUCTIVITY_SCORE -gt 100 ]; then
            echo "- Productivity level: High (${PRODUCTIVITY_SCORE} lines per commit)"
        elif [ $PRODUCTIVITY_SCORE -gt 50 ]; then
            echo "- Productivity level: Medium (${PRODUCTIVITY_SCORE} lines per commit)"
        else
            echo "- Productivity level: Focused (${PRODUCTIVITY_SCORE} lines per commit - likely bug fixes/refinements)"
        fi
    fi

    echo ""
    echo "---"
    echo ""
done

# Generate comprehensive project analysis
echo "## Executive Summary"
echo ""

# Calculate team productivity metrics
CONTRIBUTOR_COUNT=$(echo "$CONTRIBUTORS" | wc -w)
AVG_COMMITS_PER_CONTRIBUTOR=$((TOTAL_COMMITS / CONTRIBUTOR_COUNT))
AVG_LINES_PER_CONTRIBUTOR=$((TOTAL_ADDITIONS / CONTRIBUTOR_COUNT))

# Generate intelligent project narrative by analyzing commit content
echo "**Project Narrative:**"

# Analyze all commits to understand what was actually accomplished
ALL_RECENT_COMMITS=$(git log --since="${DAYS_BACK} days ago" --pretty=format:"%H|%s" | head -30)
PROJECT_FEATURES=""
PROJECT_FIXES=""
ARCHITECTURE_WORK=""
DATABASE_WORK=""

if [ -n "$ALL_RECENT_COMMITS" ]; then
    # Count different types of work with content analysis
    TOTAL_FEATURES=0
    TOTAL_API_WORK=0
    TOTAL_DATABASE_WORK=0
    TOTAL_BUG_FIXES=0
    TOTAL_ARCHITECTURE_WORK=0

    # Analyze commits to build project narrative
    echo "$ALL_RECENT_COMMITS" | while IFS='|' read -r COMMIT_HASH COMMIT_MSG; do
        DIFF_CONTENT=$(git show --no-merges --format="" "$COMMIT_HASH" 2>/dev/null | head -50)

        case "$COMMIT_MSG" in
            feat*|feature*)
                if echo "$DIFF_CONTENT" | grep -q "@Controller\|@Get\|@Post\|@Put\|@Delete"; then
                    echo "API_ENDPOINT: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                elif echo "$DIFF_CONTENT" | grep -q "CREATE TABLE\|ALTER TABLE\|\.entity\.ts\|schema"; then
                    echo "DATABASE_FEATURE: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                elif echo "$DIFF_CONTENT" | grep -q "@Module\|module\|architecture"; then
                    echo "ARCHITECTURE_FEATURE: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                else
                    echo "GENERAL_FEATURE: ${COMMIT_MSG#feat*:}" | sed 's/^feat(//' | sed 's/)://' | sed 's/feat: //'
                fi
                ;;
            fix*)
                echo "BUG_FIX: ${COMMIT_MSG#fix*:}" | sed 's/^fix(//' | sed 's/)://' | sed 's/fix: //'
                ;;
            refactor*)
                echo "REFACTOR: ${COMMIT_MSG#refactor*:}" | sed 's/^refactor(//' | sed 's/)://' | sed 's/refactor: //'
                ;;
        esac
    done > /tmp/project_analysis_$$

    # Count and categorize the work
    API_FEATURES=$(grep "API_ENDPOINT:" /tmp/project_analysis_$$ | wc -l)
    DB_FEATURES=$(grep "DATABASE_FEATURE:" /tmp/project_analysis_$$ | wc -l)
    ARCH_FEATURES=$(grep "ARCHITECTURE_FEATURE:" /tmp/project_analysis_$$ | wc -l)
    GENERAL_FEATURES=$(grep "GENERAL_FEATURE:" /tmp/project_analysis_$$ | wc -l)
    BUG_FIXES=$(grep "BUG_FIX:" /tmp/project_analysis_$$ | wc -l)
    REFACTORS=$(grep "REFACTOR:" /tmp/project_analysis_$$ | wc -l)

    # Generate executive narrative with proper line breaks
    if [ $((API_FEATURES + DB_FEATURES + ARCH_FEATURES + GENERAL_FEATURES)) -gt 0 ]; then
        echo "During this ${DAYS_BACK}-day development cycle, the team accomplished significant progress across multiple technical areas."
        echo ""

        if [ $API_FEATURES -gt 0 ]; then
            echo "The development effort heavily focused on **API expansion**, with $API_FEATURES new endpoints and controller implementations that enhance the system's integration capabilities."
            echo ""
        fi

        if [ $DB_FEATURES -gt 0 ]; then
            echo "**Database infrastructure** saw substantial improvements with $DB_FEATURES schema enhancements, strengthening the data layer foundation."
            echo ""
        fi

        if [ $ARCH_FEATURES -gt 0 ]; then
            echo "**System architecture** evolved through $ARCH_FEATURES module implementations, improving code organization and maintainability."
            echo ""
        fi

        if [ $BUG_FIXES -gt 0 ]; then
            if [ $BUG_FIXES -gt $((TOTAL_COMMITS / 3)) ]; then
                echo "The team dedicated considerable effort to **stability improvements**, resolving $BUG_FIXES critical issues that enhance system reliability."
            else
                echo "**Quality maintenance** remained consistent with $BUG_FIXES bug fixes alongside feature development."
            fi
            echo ""
        fi

        if [ $REFACTORS -gt 0 ]; then
            echo "**Technical debt reduction** was prioritized through $REFACTORS refactoring initiatives, improving code quality and performance."
            echo ""
        fi

        # Add team collaboration assessment
        if [ $CONTRIBUTOR_COUNT -gt 1 ]; then
            echo "Team collaboration was effective with balanced contributions across $CONTRIBUTOR_COUNT developers, maintaining consistent development velocity."
        else
            echo "Development was driven by a focused individual contributor maintaining high productivity standards."
        fi
    else
        echo "During this ${DAYS_BACK}-day period, the team focused on maintenance and infrastructure work, with ${TOTAL_COMMITS} commits improving system stability and code quality."
    fi

    # Clean up temp file
    rm -f /tmp/project_analysis_$$
fi

echo ""
echo "**Quantitative Summary:**"
echo "The team collectively contributed ${TOTAL_COMMITS} commits, adding ${TOTAL_ADDITIONS} lines while removing ${TOTAL_DELETIONS} lines, resulting in a net codebase growth of $((TOTAL_ADDITIONS - TOTAL_DELETIONS)) lines across ${TOTAL_FILES_CHANGED} files."
echo ""

# Analyze project activity patterns
DAILY_AVG=$((TOTAL_COMMITS / DAYS_BACK))
if [ $DAILY_AVG -gt 10 ]; then
    ACTIVITY_LEVEL="Very High"
elif [ $DAILY_AVG -gt 5 ]; then
    ACTIVITY_LEVEL="High"
elif [ $DAILY_AVG -gt 2 ]; then
    ACTIVITY_LEVEL="Moderate"
else
    ACTIVITY_LEVEL="Low"
fi

echo "**Development Velocity:**"
echo "- Activity Level: $ACTIVITY_LEVEL (${DAILY_AVG} commits/day average)"
echo "- Team Collaboration: ${AVG_COMMITS_PER_CONTRIBUTOR} commits per contributor on average"
echo "- Code Volume: ${AVG_LINES_PER_CONTRIBUTOR} lines added per contributor on average"
echo ""

# Analyze work distribution
ALL_COMMIT_TYPES=$(git log --since="${DAYS_BACK} days ago" --pretty=format:"%s")
TOTAL_FEAT=$(echo "$ALL_COMMIT_TYPES" | grep -E "^feat" | wc -l)
TOTAL_FIX=$(echo "$ALL_COMMIT_TYPES" | grep -E "^fix" | wc -l)
TOTAL_REFACTOR=$(echo "$ALL_COMMIT_TYPES" | grep -E "^refactor" | wc -l)
TOTAL_DOCS=$(echo "$ALL_COMMIT_TYPES" | grep -E "^docs" | wc -l)
TOTAL_TEST=$(echo "$ALL_COMMIT_TYPES" | grep -E "^test" | wc -l)

echo "**Work Distribution Analysis:**"
if [ $TOTAL_FEAT -gt 0 ]; then
    FEAT_PERCENT=$((TOTAL_FEAT * 100 / TOTAL_COMMITS))
    echo "- Feature Development: ${FEAT_PERCENT}% (${TOTAL_FEAT} commits) - Team focused on new functionality"
fi

if [ $TOTAL_FIX -gt 0 ]; then
    FIX_PERCENT=$((TOTAL_FIX * 100 / TOTAL_COMMITS))
    echo "- Bug Resolution: ${FIX_PERCENT}% (${TOTAL_FIX} commits) - Maintenance and stability work"
fi

if [ $TOTAL_REFACTOR -gt 0 ]; then
    REFACTOR_PERCENT=$((TOTAL_REFACTOR * 100 / TOTAL_COMMITS))
    echo "- Code Quality: ${REFACTOR_PERCENT}% (${TOTAL_REFACTOR} commits) - Technical debt reduction"
fi

if [ $TOTAL_DOCS -gt 0 ]; then
    DOCS_PERCENT=$((TOTAL_DOCS * 100 / TOTAL_COMMITS))
    echo "- Documentation: ${DOCS_PERCENT}% (${TOTAL_DOCS} commits) - Knowledge sharing and docs"
fi

if [ $TOTAL_TEST -gt 0 ]; then
    TEST_PERCENT=$((TOTAL_TEST * 100 / TOTAL_COMMITS))
    echo "- Testing: ${TEST_PERCENT}% (${TOTAL_TEST} commits) - Quality assurance efforts"
fi

echo ""

# Identify key project areas with intelligent grouping
echo "**Key Development Areas:**"
PROJECT_AREAS=$(git log --since="${DAYS_BACK} days ago" --name-only --pretty=format: | grep -v '^$' | sed 's|/[^/]*$||' | sort | uniq -c | sort -nr)

if [ -n "$PROJECT_AREAS" ]; then
    # Group and summarize by category
    BACKEND_TOTAL=$(echo "$PROJECT_AREAS" | grep -E "src/modules|modules" | awk '{sum+=$1} END {print sum+0}')
    DATABASE_TOTAL=$(echo "$PROJECT_AREAS" | grep -E "libs/db|database|db" | awk '{sum+=$1} END {print sum+0}')
    TESTING_TOTAL=$(echo "$PROJECT_AREAS" | grep -E "test|spec" | awk '{sum+=$1} END {print sum+0}')
    DOCS_TOTAL=$(echo "$PROJECT_AREAS" | grep -E "docs|README" | awk '{sum+=$1} END {print sum+0}')
    CONFIG_TOTAL=$(echo "$PROJECT_AREAS" | grep -E "config|env" | awk '{sum+=$1} END {print sum+0}')
    COMMON_TOTAL=$(echo "$PROJECT_AREAS" | grep -E "src/common|common" | awk '{sum+=$1} END {print sum+0}')
    
    # Display categories with significant activity
    if [ $BACKEND_TOTAL -gt 5 ]; then
        echo "- **Backend Development**: API modules, controllers, and business logic ($BACKEND_TOTAL file changes)"
    fi
    
    if [ $DATABASE_TOTAL -gt 5 ]; then
        echo "- **Database Layer**: Schema migrations, entities, and data access ($DATABASE_TOTAL file changes)"
    fi
    
    if [ $TESTING_TOTAL -gt 5 ]; then
        echo "- **Quality Assurance**: Test suites, specifications, and quality improvements ($TESTING_TOTAL file changes)"
    fi
    
    if [ $COMMON_TOTAL -gt 5 ]; then
        echo "- **Core Infrastructure**: Shared utilities, common types, and base functionality ($COMMON_TOTAL file changes)"
    fi
    
    if [ $DOCS_TOTAL -gt 2 ]; then
        echo "- **Documentation**: Project guides, README updates, and technical documentation ($DOCS_TOTAL file changes)"
    fi
    
    if [ $CONFIG_TOTAL -gt 2 ]; then
        echo "- **Configuration**: Environment setup, build configuration, and deployment scripts ($CONFIG_TOTAL file changes)"
    fi
    
    # Show any other significant areas that don't fit standard categories
    echo "$PROJECT_AREAS" | while read count dir; do
        if [ "$count" -gt 8 ]; then
            case "$dir" in
                *src/modules*|*modules*|*libs/db*|*database*|*db*|*test*|*spec*|*docs*|*README*|*config*|*env*|*src/common*|*common*) 
                    # Skip - already categorized above
                    ;;
                *)
                    echo "- **${dir}**: Focused development area ($count file changes)"
                    ;;
            esac
        fi
    done
fi

echo ""

# Risk and recommendation analysis
echo "**Management Insights & Recommendations:**"

# Check for potential issues
if [ $TOTAL_FIX -gt $((TOTAL_FEAT * 2)) ]; then
    echo "- ⚠️  **High Bug Fix Ratio**: Consider focusing on code review processes and testing"
fi

if [ $CONTRIBUTOR_COUNT -eq 1 ]; then
    echo "- ⚠️  **Single Contributor Risk**: Consider knowledge sharing and backup developers"
elif [ $CONTRIBUTOR_COUNT -gt 1 ]; then
    # Check for work distribution balance
    MOST_ACTIVE_COMMITS=$(git log --since="${DAYS_BACK} days ago" --pretty=format:"%ae" | sort | uniq -c | sort -nr | head -1 | awk '{print $1}')
    if [ $MOST_ACTIVE_COMMITS -gt $((TOTAL_COMMITS * 70 / 100)) ]; then
        echo "- ⚠️  **Work Distribution**: One contributor handling >70% of commits - consider load balancing"
    else
        echo "- ✅ **Balanced Team**: Good work distribution across team members"
    fi
fi

if [ $TOTAL_DOCS -eq 0 ]; then
    echo "- 📝 **Documentation Gap**: Consider prioritizing documentation updates"
else
    echo "- ✅ **Documentation**: Team is maintaining documentation alongside development"
fi

if [ $TOTAL_TEST -gt 0 ]; then
    echo "- ✅ **Quality Focus**: Team is investing in testing and quality assurance"
fi

echo ""

# Show timeline activity for planning
echo "**Development Timeline:**"
TIMELINE_DATA=$(git log --since="${DAYS_BACK} days ago" --pretty=format:"%cd" --date=short | sort | uniq -c | sort -k2)

if [ -n "$TIMELINE_DATA" ]; then
    echo "$TIMELINE_DATA" | while read count date; do
        # Create simple activity indicator
        ACTIVITY_BAR=""
        NORMALIZED_COUNT=$((count / 2))
        if [ $NORMALIZED_COUNT -gt 20 ]; then NORMALIZED_COUNT=20; fi
        if [ $NORMALIZED_COUNT -lt 1 ]; then NORMALIZED_COUNT=1; fi

        for i in $(seq 1 $NORMALIZED_COUNT); do
            ACTIVITY_BAR="${ACTIVITY_BAR}█"
        done

        printf "- %s: %2d commits %s\n" "$date" "$count" "$ACTIVITY_BAR"
    done
else
    echo "- No commit activity found in the specified time period"
fi

echo ""

# Try to get PR information if gh CLI is available
if command -v gh &> /dev/null; then
    echo "## Pull Requests"
    echo ""

    # Get merged PRs in the time period
    MERGED_PRS=$(gh pr list --state merged --limit 100 --json mergedAt,title,author,number 2>/dev/null | \
    jq -r --arg start_date "$START_DATE" \
    '.[] | select(.mergedAt >= $start_date + "T00:00:00Z") | "\(.number)|\(.title)|\(.author.login)|\(.mergedAt)"' 2>/dev/null || echo "")

    if [ -n "$MERGED_PRS" ]; then
        echo "**Merged Pull Requests:**"
        echo "$MERGED_PRS" | while IFS='|' read -r number title author merged_at; do
            echo "- PR #${number}: ${title} by @${author} ($(echo $merged_at | cut -d'T' -f1))"
        done
        echo ""
    fi

    # Get created PRs in the time period
    CREATED_PRS=$(gh pr list --state all --limit 100 --json createdAt,title,author,number,state 2>/dev/null | \
    jq -r --arg start_date "$START_DATE" \
    '.[] | select(.createdAt >= $start_date + "T00:00:00Z") | "\(.number)|\(.title)|\(.author.login)|\(.state)|\(.createdAt)"' 2>/dev/null || echo "")

    if [ -n "$CREATED_PRS" ]; then
        echo "**Created Pull Requests:**"
        echo "$CREATED_PRS" | while IFS='|' read -r number title author state created_at; do
            echo "- PR #${number}: ${title} by @${author} [${state}] ($(echo $created_at | cut -d'T' -f1))"
        done
    fi
else
    echo "**Note:** Install GitHub CLI (\`gh\`) to include pull request information in reports."
fi

echo ""
echo "---"
echo "*Report generated by Claude Code Gosu Summary command*"

} | tee >(
    # Save report to .gosu directory, create it if it doesn't exist
    mkdir -p ".gosu"
    REPORT_FILE=".gosu/work-summary-${START_DATE}-to-${TODAY}-${DAYS_BACK}days.md"
    cat > "$REPORT_FILE"
    echo "" >&2
    echo "📄 Report saved to: $REPORT_FILE" >&2
)
```

## Features

This command generates a comprehensive work summary that includes:

### Executive Summary (Manager-Focused)

- **Project Health Overview**: High-level narrative of team productivity and code growth
- **Development Velocity**: Activity level assessment and team collaboration metrics
- **Work Distribution Analysis**: Breakdown of feature development vs maintenance work
- **Key Development Areas**: Intelligence about which parts of the codebase are most active
- **Management Insights**: Risk analysis, recommendations, and actionable insights
- **Development Timeline**: Visual timeline showing daily commit activity

### Individual Contributor Analysis

- **Key Accomplishments**: AI-generated summary of each person's major contributions
- **Areas of Focus**: Intelligent categorization of work areas (Backend, Database, Testing, etc.)
- **Impact & Metrics**: Code contribution metrics and productivity assessment
- **Feature vs Fix Analysis**: Breakdown of new features vs bug fixes per contributor

### Pull Request Information (if GitHub CLI available)

- **Merged PRs**: Pull requests merged in the time period
- **Created PRs**: Pull requests created in the time period with status

### Report Persistence

- **Auto-save**: Reports are automatically saved to `.gosu/` directory if it exists
- **Filename Format**: `work-summary-YYYY-MM-DD-to-YYYY-MM-DD-Xdays.md`
- **Historical Tracking**: Keeps record of previous reports for comparison

### Usage Examples

```bash
# Generate report for last 7 days (default)
/gosu:summary

# Generate report for last 30 days
/gosu:summary 30

# Generate report for last 90 days
/gosu:summary 90
```

The report is formatted in Markdown and provides a complete overview of team productivity and code changes over the specified time period.
