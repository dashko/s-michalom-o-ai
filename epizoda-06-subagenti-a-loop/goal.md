/goal set Enhance commit-message generation using required Git file history.
Keep the funny message and factual summary; add affected components,
use cases, and recommended tests. Block generation if history is unavailable.

Milestones:
1) History: retrieve relevant previous commits and patches from the diff's
base revision, follow renames, limit context size, and separate history
from the current diff.
2) Summary: explain how current changes introduce, extend, fix, replace,
or reverse behavior. Group related changes across files. Keep historical
and new work distinct; do not invent intent.
3) Impact: inspect callers, dependencies, documentation, and existing tests.
Identify affected components and use cases, distinguishing confirmed
changes from possible effects. Recommend prioritized test scenarios
with inputs, expected results, rationale, and existing tests or coverage
gaps. State uncertainty.
4) Evidence: add optional supporting commit references. Test history
selection, missing history, renames, context limits, and shared
dependencies. Demonstrate real generated output with accurate summaries
and actionable test recommendations.

Testing:
Ollama listens here http://10.8.0.3:11434/v1 and model qwen3.8:27b
You can try it on repository d3, it is in this directory.

Workflow:
Deliver milestones sequentially. Invoke a fresh implementator subagent to implement,
add tests, and run format, lint, typecheck, build, and tests.
Wait, then invoke a fresh reviewer subagent. Give both full task context; give
reviewer subagent the current diff and actual check results.
Review active and completed milestones only.
PASS advances. FAIL gets one repair attempt followed by review.
A second FAIL or required user input stops the goal as blocked,
with issues and next actions.

Done:
All four milestones pass review, final review covers the whole task,
and all applicable checks pass on final code with recorded output.

