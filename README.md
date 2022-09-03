# :shell: ShellExecutor

Simple shell executor with Swift.

![Test](https://github.com/taji-taji/swift-shell-executor/actions/workflows/test.yml/badge.svg)
[![MIT License](https://img.shields.io/github/license/taji-taji/swift-shell-executor)](https://github.com/taji-taji/DangerSwiftPeriphery/blob/main/LICENSE)
[![Latest Version](https://img.shields.io/github/v/release/taji-taji/swift-shell-executor?label=latest%20version)](https://github.com/taji-taji/DangerSwiftPeriphery/releases/latest)

## Requirements

- Swift 5.5.2 or later

## Usage

### Package.swift

To use the `ShellExecutor` library in a SwiftPM project, add the following line to the dependencies in your `Package.swift` file:

```swift
.package(url: "https://github.com/taji-taji/swift-shell-executor.git", from: "1.0.0")
```

Include `"ShellExecutor"` as a dependency for your executable target:

```swift
.target(name: "<target>", dependencies: [
    .product(name: "ShellExecutor", package: "swift-shell-executor"),
]),
```
Finally, add `import ShellExecutor` to your source code.

### Example

```swift
import ShellExecutor

let shell = ShellExecutor()

do {
    // ShellExecutor is implemented with `callAsFunction`.
    let output = try shell("ls", arguments: ["-l", "-a"])
    print(output)
} catch {
    print(error)
}
```

Execute with some Environment Variables. 

```swift
try shell("brew install git",
          additionalEnvironment: ["HOMEBREW_NO_AUTO_UPDATE": "1"])
```
