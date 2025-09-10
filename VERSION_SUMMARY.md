# 📜 Full File Version History

## 🔹 .github/workflows/your-workflow-name.yml

- **f90e40d**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
- **f688e22**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
- **42c398c**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
- **2c38457**: Create your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
**Recent Changes Preview:**
```diff
diff --git a/.github/workflows/your-workflow-name.yml b/.github/workflows/your-workflow-name.yml
index a9b8fe7..79f6428 100644
--- a/.github/workflows/your-workflow-name.yml
+++ b/.github/workflows/your-workflow-name.yml
@@ -1,4 +1,4 @@
-name: Version Summary
+name: Full Version History Summary
 
 on:
   push:
@@ -15,19 +15,32 @@ jobs:
       - name: Checkout code
         uses: actions/checkout@v3
         with:
-          fetch-depth: 0  # Ensures full commit history is available
+          fetch-depth: 0  # Required to access full commit history
 
-      - name: Generate enhanced version summary
+      - name: Generate full version history summary
         run: |
-          echo "# 📄 File Version Summary" > VERSION_SUMMARY.md
+          echo "# 📜 Full File Version History" > VERSION_SUMMARY.md
           echo "" >> VERSION_SUMMARY.md
-          for file in $(git diff --name-only HEAD~1); do
+
+          for file in $(git ls-files); do
             echo "## 🔹 $file" >> VERSION_SUMMARY.md
-            commit=$(git log -1 --pretty=format:"**Last Commit**: %s (%ad by %an)" --date=short -- "$file")
-            echo "$commit" >> VERSION_SUMMARY.md
-            echo "**Changes:**" >> VERSION_SUMMARY.md
+            echo "" >> VERSION_SUMMARY.md
+
+            # List all commits that modified this file
+            git log --pretty=format:"- **%h**: %s (%ad by %an)" --date=short -- "$file" >> VERSION_SUMMARY.md
+
+            echo "" >> VERSION_SUMMARY.md
+            echo "**Recent Changes Preview:**" >> VERSION_SUMMARY.md
             echo '```diff' >> VERSION_SUMMARY.md
-            git diff HEAD~1 -- "$file" >> VERSION_SUMMARY.md
+
+            # Show diff between last two commits that touched this file
+            commits=($(git log --pretty=format:"%H" -- "$file"))
+            if [ ${#commits[@]} -ge 2 ]; then
+              git diff ${commits[1]} ${commits[0]} -- "$file" >> VERSION_SUMMARY.md
+            else
+              echo "# No previous version to compare." >> VERSION_SUMMARY.md
+            fi
+
             echo '```' >> VERSION_SUMMARY.md
             echo "" >> VERSION_SUMMARY.md
           done
@@ -37,5 +50,5 @@ jobs:
           git config user.name "GitHub Action"
           git config user.email "action@github.com"
           git add VERSION_SUMMARY.md
-          git commit -m "Update version summary"
+          git commit -m "Update full version history summary"
           git push
```

## 🔹 CALA


**Recent Changes Preview:**
```diff
# No previous version to compare.
```

## 🔹 Shared


**Recent Changes Preview:**
```diff
# No previous version to compare.
```

## 🔹 Service


**Recent Changes Preview:**
```diff
# No previous version to compare.
```

## 🔹 (1).pbix


**Recent Changes Preview:**
```diff
# No previous version to compare.
```

## 🔹 VERSION_SUMMARY.md

- **886766d**: Update full version history summary (2025-09-10 by GitHub Action)
- **d0156da**: Update version summary (2025-09-10 by GitHub Action)
- **53ff3a1**: Update version summary (2025-09-10 by GitHub Action)
**Recent Changes Preview:**
```diff
diff --git a/VERSION_SUMMARY.md b/VERSION_SUMMARY.md
index 0751415..c3cc3d0 100644
--- a/VERSION_SUMMARY.md
+++ b/VERSION_SUMMARY.md
@@ -1,52 +1,116 @@
-# 📄 File Version Summary
+# 📜 Full File Version History
 
 ## 🔹 .github/workflows/your-workflow-name.yml
-**Last Commit**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
-**Changes:**
+
+- **f90e40d**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
+- **f688e22**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
+- **42c398c**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
+- **2c38457**: Create your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
+**Recent Changes Preview:**
 ```diff
 diff --git a/.github/workflows/your-workflow-name.yml b/.github/workflows/your-workflow-name.yml
-index f894d01..a9b8fe7 100644
+index a9b8fe7..79f6428 100644
 --- a/.github/workflows/your-workflow-name.yml
 +++ b/.github/workflows/your-workflow-name.yml
-@@ -15,14 +15,21 @@ jobs:
+@@ -1,4 +1,4 @@
+-name: Version Summary
++name: Full Version History Summary
+ 
+ on:
+   push:
+@@ -15,19 +15,32 @@ jobs:
        - name: Checkout code
          uses: actions/checkout@v3
          with:
--          fetch-depth: 0
-+          fetch-depth: 0  # Ensures full commit history is available
+-          fetch-depth: 0  # Ensures full commit history is available
++          fetch-depth: 0  # Required to access full commit history
  
--      - name: Generate version summary
-+      - name: Generate enhanced version summary
+-      - name: Generate enhanced version summary
++      - name: Generate full version history summary
          run: |
--          echo "# File Version Summary" > VERSION_SUMMARY.md
--          for file in $(git ls-files); do
--            commit=$(git log -1 --pretty=format:"%s (%ad by %an)" --date=short -- "$file")
--            echo "- **$file**: $commit" >> VERSION_SUMMARY.md
-+          echo "# 📄 File Version Summary" > VERSION_SUMMARY.md
-+          echo "" >> VERSION_SUMMARY.md
-+          for file in $(git diff --name-only HEAD~1); do
-+            echo "## 🔹 $file" >> VERSION_SUMMARY.md
-+            commit=$(git log -1 --pretty=format:"**Last Commit**: %s (%ad by %an)" --date=short -- "$file")
-+            echo "$commit" >> VERSION_SUMMARY.md
-+            echo "**Changes:**" >> VERSION_SUMMARY.md
-+            echo '```diff' >> VERSION_SUMMARY.md
-+            git diff HEAD~1 -- "$file" >> VERSION_SUMMARY.md
-+            echo '```' >> VERSION_SUMMARY.md
+-          echo "# 📄 File Version Summary" > VERSION_SUMMARY.md
++          echo "# 📜 Full File Version History" > VERSION_SUMMARY.md
+           echo "" >> VERSION_SUMMARY.md
+-          for file in $(git diff --name-only HEAD~1); do
++
++          for file in $(git ls-files); do
+             echo "## 🔹 $file" >> VERSION_SUMMARY.md
+-            commit=$(git log -1 --pretty=format:"**Last Commit**: %s (%ad by %an)" --date=short -- "$file")
+-            echo "$commit" >> VERSION_SUMMARY.md
+-            echo "**Changes:**" >> VERSION_SUMMARY.md
++            echo "" >> VERSION_SUMMARY.md
++
++            # List all commits that modified this file
++            git log --pretty=format:"- **%h**: %s (%ad by %an)" --date=short -- "$file" >> VERSION_SUMMARY.md
++
 +            echo "" >> VERSION_SUMMARY.md
++            echo "**Recent Changes Preview:**" >> VERSION_SUMMARY.md
+             echo '```diff' >> VERSION_SUMMARY.md
+-            git diff HEAD~1 -- "$file" >> VERSION_SUMMARY.md
++
++            # Show diff between last two commits that touched this file
++            commits=($(git log --pretty=format:"%H" -- "$file"))
++            if [ ${#commits[@]} -ge 2 ]; then
++              git diff ${commits[1]} ${commits[0]} -- "$file" >> VERSION_SUMMARY.md
++            else
++              echo "# No previous version to compare." >> VERSION_SUMMARY.md
++            fi
++
+             echo '```' >> VERSION_SUMMARY.md
+             echo "" >> VERSION_SUMMARY.md
            done
- 
-       - name: Commit version summary
+@@ -37,5 +50,5 @@ jobs:
+           git config user.name "GitHub Action"
+           git config user.email "action@github.com"
+           git add VERSION_SUMMARY.md
+-          git commit -m "Update version summary"
++          git commit -m "Update full version history summary"
+           git push
+```
+
+## 🔹 CALA
+
+
+**Recent Changes Preview:**
+```diff
+# No previous version to compare.
+```
+
+## 🔹 Shared
+
+
+**Recent Changes Preview:**
+```diff
+# No previous version to compare.
+```
+
+## 🔹 Service
+
+
+**Recent Changes Preview:**
+```diff
+# No previous version to compare.
+```
+
+## 🔹 (1).pbix
+
+
+**Recent Changes Preview:**
+```diff
+# No previous version to compare.
 ```
 
 ## 🔹 VERSION_SUMMARY.md
-**Last Commit**: Update version summary (2025-09-10 by GitHub Action)
-**Changes:**
+
+- **d0156da**: Update version summary (2025-09-10 by GitHub Action)
+- **53ff3a1**: Update version summary (2025-09-10 by GitHub Action)
+**Recent Changes Preview:**
 ```diff
 diff --git a/VERSION_SUMMARY.md b/VERSION_SUMMARY.md
-index 4daab62..bd22af2 100644
+index 4daab62..0751415 100644
 --- a/VERSION_SUMMARY.md
 +++ b/VERSION_SUMMARY.md
-@@ -1,6 +1,44 @@
+@@ -1,6 +1,101 @@
 -# File Version Summary
 -- **.github/workflows/your-workflow-name.yml**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
 -- **CALA**: 
@@ -97,5 +161,62 @@ index 4daab62..bd22af2 100644
 +**Last Commit**: Update version summary (2025-09-10 by GitHub Action)
 +**Changes:**
 +```diff
++diff --git a/VERSION_SUMMARY.md b/VERSION_SUMMARY.md
++index 4daab62..bd22af2 100644
++--- a/VERSION_SUMMARY.md
+++++ b/VERSION_SUMMARY.md
++@@ -1,6 +1,44 @@
++-# File Version Summary
++-- **.github/workflows/your-workflow-name.yml**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
++-- **CALA**: 
++-- **Shared**: 
++-- **Service**: 
++-- **(1).pbix**: 
+++# 📄 File Version Summary
+++
+++## 🔹 .github/workflows/your-workflow-name.yml
+++**Last Commit**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
+++**Changes:**
+++```diff
+++diff --git a/.github/workflows/your-workflow-name.yml b/.github/workflows/your-workflow-name.yml
+++index f894d01..a9b8fe7 100644
+++--- a/.github/workflows/your-workflow-name.yml
++++++ b/.github/workflows/your-workflow-name.yml
+++@@ -15,14 +15,21 @@ jobs:
+++       - name: Checkout code
+++         uses: actions/checkout@v3
+++         with:
+++-          fetch-depth: 0
++++          fetch-depth: 0  # Ensures full commit history is available
+++ 
+++-      - name: Generate version summary
++++      - name: Generate enhanced version summary
+++         run: |
+++-          echo "# File Version Summary" > VERSION_SUMMARY.md
+++-          for file in $(git ls-files); do
+++-            commit=$(git log -1 --pretty=format:"%s (%ad by %an)" --date=short -- "$file")
+++-            echo "- **$file**: $commit" >> VERSION_SUMMARY.md
++++          echo "# 📄 File Version Summary" > VERSION_SUMMARY.md
++++          echo "" >> VERSION_SUMMARY.md
++++          for file in $(git diff --name-only HEAD~1); do
++++            echo "## 🔹 $file" >> VERSION_SUMMARY.md
++++            commit=$(git log -1 --pretty=format:"**Last Commit**: %s (%ad by %an)" --date=short -- "$file")
++++            echo "$commit" >> VERSION_SUMMARY.md
++++            echo "**Changes:**" >> VERSION_SUMMARY.md
++++            echo '```diff' >> VERSION_SUMMARY.md
++++            git diff HEAD~1 -- "$file" >> VERSION_SUMMARY.md
++++            echo '```' >> VERSION_SUMMARY.md
++++            echo "" >> VERSION_SUMMARY.md
+++           done
+++ 
+++       - name: Commit version summary
+++```
+++
+++## 🔹 VERSION_SUMMARY.md
+++**Last Commit**: Update version summary (2025-09-10 by GitHub Action)
+++**Changes:**
+++```diff
++```
++
 ```
 
```

