---
"cn": patch
---

Fix broken type declarations in the published package. `cn/config` types resolved to an internal bundler chunk with mangled export names (`defaultConfig`, `mergeConfigs`, `createCn`, `fromTheme`, and the rest of the surface were missing or renamed to single letters), and `cn/lite` declared `clsx()` with no parameters, rejecting every real call. Runtime behavior was unaffected. The build now type-checks every entry's declarations through the real `exports` map (both the `import` and `require` conditions), so a regression fails the build instead of publishing.
