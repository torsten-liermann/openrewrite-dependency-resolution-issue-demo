# openrewrite-dependency-resolution-issue-demo
This small Maven project demonstrates a nested dependency management setup. The nesting occurs because a second dependency management section adjusts the scope of dependencies defined in a first dependency management section. While this mechanism is not explicitly documented in Maven's official documentation, it is used in a real-world project—even if this "trick" is not something to be celebrated. It is what it is.

What is particularly noteworthy in the second dependency management section is the absence of version information for the dependencies. Maven has no issue with this and correctly uses the version numbers from the first dependency management section. However, OpenRewrite (specifically the `maven-rewrite` module in version 8.42.4) encounters a problem and fails to process these dependencies.

In this example, the issue is clearly visualized, making it easier to understand. However, in the aforementioned real-world project with thousands of POM files, OpenRewrite abruptly terminates processing without providing a specific error message. This behavior makes troubleshooting and resolving the issue significantly more challenging.

The request to the OpenRewrite developers is simple: Please implement the behavior of Maven 3.9.9, which handles this case gracefully without failing. By aligning with Maven's behavior, OpenRewrite can better support projects with complex dependency management setups like this one.

