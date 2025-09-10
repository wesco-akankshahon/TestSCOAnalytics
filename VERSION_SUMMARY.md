# 📄 File Version Summary

## 🔹 .github/workflows/your-workflow-name.yml
**Last Commit**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
**Changes:**
```diff
diff --git a/.github/workflows/your-workflow-name.yml b/.github/workflows/your-workflow-name.yml
index f894d01..a9b8fe7 100644
--- a/.github/workflows/your-workflow-name.yml
+++ b/.github/workflows/your-workflow-name.yml
@@ -15,14 +15,21 @@ jobs:
       - name: Checkout code
         uses: actions/checkout@v3
         with:
-          fetch-depth: 0
+          fetch-depth: 0  # Ensures full commit history is available
 
-      - name: Generate version summary
+      - name: Generate enhanced version summary
         run: |
-          echo "# File Version Summary" > VERSION_SUMMARY.md
-          for file in $(git ls-files); do
-            commit=$(git log -1 --pretty=format:"%s (%ad by %an)" --date=short -- "$file")
-            echo "- **$file**: $commit" >> VERSION_SUMMARY.md
+          echo "# 📄 File Version Summary" > VERSION_SUMMARY.md
+          echo "" >> VERSION_SUMMARY.md
+          for file in $(git diff --name-only HEAD~1); do
+            echo "## 🔹 $file" >> VERSION_SUMMARY.md
+            commit=$(git log -1 --pretty=format:"**Last Commit**: %s (%ad by %an)" --date=short -- "$file")
+            echo "$commit" >> VERSION_SUMMARY.md
+            echo "**Changes:**" >> VERSION_SUMMARY.md
+            echo '```diff' >> VERSION_SUMMARY.md
+            git diff HEAD~1 -- "$file" >> VERSION_SUMMARY.md
+            echo '```' >> VERSION_SUMMARY.md
+            echo "" >> VERSION_SUMMARY.md
           done
 
       - name: Commit version summary
```

## 🔹 VERSION_SUMMARY.md
**Last Commit**: Update version summary (2025-09-10 by GitHub Action)
**Changes:**
```diff
diff --git a/VERSION_SUMMARY.md b/VERSION_SUMMARY.md
index 4daab62..bd22af2 100644
--- a/VERSION_SUMMARY.md
+++ b/VERSION_SUMMARY.md
@@ -1,6 +1,44 @@
-# File Version Summary
-- **.github/workflows/your-workflow-name.yml**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
-- **CALA**: 
-- **Shared**: 
-- **Service**: 
-- **(1).pbix**: 
+# 📄 File Version Summary
+
+## 🔹 .github/workflows/your-workflow-name.yml
+**Last Commit**: Update your-workflow-name.yml (2025-09-10 by wesco-akankshahon)
+**Changes:**
+```diff
+diff --git a/.github/workflows/your-workflow-name.yml b/.github/workflows/your-workflow-name.yml
+index f894d01..a9b8fe7 100644
+--- a/.github/workflows/your-workflow-name.yml
++++ b/.github/workflows/your-workflow-name.yml
+@@ -15,14 +15,21 @@ jobs:
+       - name: Checkout code
+         uses: actions/checkout@v3
+         with:
+-          fetch-depth: 0
++          fetch-depth: 0  # Ensures full commit history is available
+ 
+-      - name: Generate version summary
++      - name: Generate enhanced version summary
+         run: |
+-          echo "# File Version Summary" > VERSION_SUMMARY.md
+-          for file in $(git ls-files); do
+-            commit=$(git log -1 --pretty=format:"%s (%ad by %an)" --date=short -- "$file")
+-            echo "- **$file**: $commit" >> VERSION_SUMMARY.md
++          echo "# 📄 File Version Summary" > VERSION_SUMMARY.md
++          echo "" >> VERSION_SUMMARY.md
++          for file in $(git diff --name-only HEAD~1); do
++            echo "## 🔹 $file" >> VERSION_SUMMARY.md
++            commit=$(git log -1 --pretty=format:"**Last Commit**: %s (%ad by %an)" --date=short -- "$file")
++            echo "$commit" >> VERSION_SUMMARY.md
++            echo "**Changes:**" >> VERSION_SUMMARY.md
++            echo '```diff' >> VERSION_SUMMARY.md
++            git diff HEAD~1 -- "$file" >> VERSION_SUMMARY.md
++            echo '```' >> VERSION_SUMMARY.md
++            echo "" >> VERSION_SUMMARY.md
+           done
+ 
+       - name: Commit version summary
+```
+
+## 🔹 VERSION_SUMMARY.md
+**Last Commit**: Update version summary (2025-09-10 by GitHub Action)
+**Changes:**
+```diff
```

