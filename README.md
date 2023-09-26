# Missing Android Resource Demo

Demo of https://github.com/bazelbuild/rules_android/issues/77.

To reproduce, run:
```
$ USE_BAZEL_VERSION=last_green bazelisk build --fat_apk_cpu=arm64-v8a --android_crosstool_top=@androidndk//:toolchain  //app/src/main:app
```

Missing resource errors look like:
```
Output:
error: resource style/Theme.AppCompat.Light.DarkActionBar (aka com.example.android.bazel:style/Theme.AppCompat.Light.DarkActionBar) not found.
app/src/main/res/values/styles.xml:6: error: style attribute 'attr/colorPrimary (aka com.example.android.bazel:attr/colorPrimary)' not found.
app/src/main/res/values/styles.xml:7: error: style attribute 'attr/colorPrimaryDark (aka com.example.android.bazel:attr/colorPrimaryDark)' not found.
app/src/main/res/values/styles.xml:8: error: style attribute 'attr/colorAccent (aka com.example.android.bazel:attr/colorAccent)' not found.
error: failed linking references.
```
