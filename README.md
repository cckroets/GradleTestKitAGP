# GradleTestKitAGP
Repro of build issue with AGP 7.3.0-alpha04

When using GradleTestKit, the build fails when using AGP version 7.3.0-alpha04, but passes with alpha03.

The task `mergeDebugAndroidTestAssets` fails when running `:assembleDebugAndroidTest` for the app module.

Stacktrace is an assertion:
```
    FAILURE: Build failed with an exception.

    * What went wrong:
    Execution failed for task ':mergeDebugAndroidTestAssets'.
    > Assertion failed


 Caused by: java.lang.AssertionError: Assertion failed
        at com.android.build.gradle.tasks.MergeSourceSetFolders.computeAssetSetList$gradle_core(MergeSourceSetFolders.kt:300)
        at com.android.build.gradle.tasks.MergeSourceSetFolders.doFullTaskAction(MergeSourceSetFolders.kt:119)
        at com.android.build.gradle.internal.tasks.IncrementalTask.handleIncrementalInputs(IncrementalTask.kt:112)
        at com.android.build.gradle.internal.tasks.IncrementalTask.access$handleIncrementalInputs(IncrementalTask.kt:65)
        at com.android.build.gradle.internal.tasks.IncrementalTask$taskAction$$inlined$recordTaskAction$1.invoke(BaseTask.kt:65)
        at com.android.build.gradle.internal.tasks.Blocks.recordSpan(Blocks.java:51)
        at com.android.build.gradle.internal.tasks.IncrementalTask.taskAction$gradle_core(IncrementalTask.kt:142)
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at org.gradle.internal.reflect.JavaMethod.invoke(JavaMethod.java:104)
        at org.gradle.api.internal.project.taskfactory.IncrementalTaskInputsTaskAction.doExecute(IncrementalTaskInputsTaskAction.java:47)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:51)
        at org.gradle.api.internal.project.taskfactory.AbstractIncrementalTaskAction.execute(AbstractIncrementalTaskAction.java:25)
        at org.gradle.api.internal.project.taskfactory.StandardTaskAction.execute(StandardTaskAction.java:29)
        at org.gradle.api.internal.tasks.execution.TaskExecution$3.run(TaskExecution.java:242)

```

