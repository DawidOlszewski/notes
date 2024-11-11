### Structure of Unified Diff Notation

Here’s an example of a diff output:

```diff
diff --git a/file.txt b/file.txt
index abc123..def456 100644
--- a/file.txt
+++ b/file.txt
@@ -1,5 +1,5 @@
 Line 1
-Line 2
+Modified Line 2
 Line 3
-Line 4
+Added new Line 4
 Line 5
```

Let’s look at each part in detail.

---

### 1. **Diff Headers**

The first few lines contain metadata about the diff:

- **`diff --git a/file.txt b/file.txt`**: Specifies the file being compared (`a/file.txt` and `b/file.txt`). The `a/` and `b/` prefixes are conventionally used to show the "before" (a) and "after" (b) versions.

- **`index abc123..def456 100644`**: This shows the hash values of each file version (useful for tracking specific commits), followed by the file permissions (e.g., `100644`).

- **`--- a/file.txt`** and **`+++ b/file.txt`**: These lines identify the "before" and "after" files. `---` represents the old version, and `+++` represents the new version.

---

### 2. **The `@@` Line (Chunk Header)**

The `@@` line shows which lines in the file are affected:

- **`@@ -1,5 +1,5 @@`**: This is the chunk header. It indicates where changes begin and how many lines are affected.
  - `-1,5`: The chunk starts at line 1 in the old file and includes 5 lines.
  - `+1,5`: The chunk starts at line 1 in the new file and includes 5 lines.

### 3. **Line-by-Line Differences**

After the `@@` line, the actual changes are shown:

- Lines with no symbol: These lines are **unchanged**.
- Lines starting with `-`: These lines were **removed** in the new version.
- Lines starting with `+`: These lines were **added** in the new version.

In our example:

```diff
 Line 1
-Line 2
+Modified Line 2
 Line 3
-Line 4
+Added new Line 4
 Line 5
```

- `Line 1`, `Line 3`, and `Line 5` are **unchanged**.
- `Line 2` was removed and replaced with `Modified Line 2`.
- `Line 4` was removed and replaced with `Added new Line 4`.