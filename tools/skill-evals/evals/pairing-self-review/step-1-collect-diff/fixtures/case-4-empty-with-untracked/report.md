<!-- SPDX-License-Identifier: Apache-2.0
     https://www.apache.org/licenses/LICENSE-2.0 -->

Invocation: (no arguments — use defaults)

git merge-base HEAD origin/main → d82f6b1
git rev-parse HEAD → d82f6b1

git diff --stat d82f6b1:
(no output — empty diff)

git ls-files --others --exclude-standard:
notes/todo.md
scripts/try_patch.py

git diff d82f6b1:
(empty)
