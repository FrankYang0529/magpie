<!-- SPDX-License-Identifier: Apache-2.0
     https://www.apache.org/licenses/LICENSE-2.0 -->

Invocation: (no arguments — use defaults)

git merge-base HEAD origin/main → c41e2a7
git rev-parse HEAD → c41e2a7

git status --short:
M  src/cache/lru.py
 M docs/cache.md

git diff --stat c41e2a7..HEAD:
(no output — HEAD is the merge base, so nothing is committed on the branch yet)

git diff --stat c41e2a7:
 docs/cache.md    | 4 +++-
 src/cache/lru.py | 9 +++++++--
 2 files changed, 10 insertions(+), 3 deletions(-)

git ls-files --others --exclude-standard:
(no output)

git diff c41e2a7 (truncated for metadata step):
diff --git a/src/cache/lru.py b/src/cache/lru.py
--- a/src/cache/lru.py
+++ b/src/cache/lru.py
@@ -31,8 +31,13 @@ class LRUCache:
     def get(self, key):
-        value = self._data.pop(key)
-        self._data[key] = value
+        try:
+            value = self._data.pop(key)
+        except KeyError:
+            return None
+        self._data[key] = value
         return value
