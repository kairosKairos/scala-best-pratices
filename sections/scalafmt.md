## 1. scalafmt 


__For more details about this section, go to scalafmt documetation https://scalameta.org/scalafmt/docs__

### 1.1 Definition

It is a tool that allows you to format your code so that it is consistent between team members.

__Pros__:

- Easy to handle
- Well done documentation
- Configurable

__Cons__: 

- Perdormances issues

Scalafmt is 6x slower than Scalariform. For 98% of source files this won't be a problem if you have a decently modern laptop. However, if you only work in files with 4.000 LOC it might be a problem. I'm quite sure that micro-optimizations can squeeze out at least ~2x performance improvements, maybe even more. Moreover, I think incremental formatting has the possibility to increase the performance by several orders of magnitude in interactive IDE environments where scalafmt is invoked on file save.

- Non-idempotent

This means you should be careful about enforcing scalafmt in your CI build.

### 1.2 Configuration

Configuration for scalafmt is defined in a plain text file .scalafmt.conf using HOCON syntax.

Here is an example .scalafmt.conf:

```
align.preset = more    // For pretty alignment.
maxColumn = 100 // For my wide 30" display.
```
#### Most popular
maxColumn
Default: `maxColumn = 80`

Keep in mind that 80 characters fit perfectly on a split laptop screen with regular resolution.
GitHub mobile view only shows 80 characters and sometimes you might review code on your phone.
Consider refactoring your code before of choosing a value above 100.


### 1.3 Implementation on IntelliJ

The Scala plugin compatible with recent versions of IntelliJ IDEA has built-in support for Scalafmt (see Note below). DO NOT install the deprecated Scalafmt plugin unless you have an older version of Intellij.

When opening a project that contains a .scalafmt.conf file, you will be prompted to use it:

![IMAGE](/repository/assets/employee.png?raw=true "IMAGE")

Choose the scalafmt formatter and IntelliJ's Reformat Code action will then use Scalafmt when formatting files. See below for shortcuts.

***Note: IntelliJ 2019.1 or later is required in order for the Scala plugin to support Scalafmt and the dynamic version set in your .scalafmt.conf. If you must use an older version, see the FAQ for an alternative.***

#### Format current file

Opt + cmd + L (macOs)
Crtl + Alt + L (Other)

To re-configure the shortcut:
- Open Preferences > Keymap
- Search for "Reformat Code"

##### Range formatting
Scalafmt is primarily designed to operate on entire text files—formatting selected ranges of code may produce undesirable results. For this reason, IntelliJ uses its own formatter for ranges by default. It is not recommended to change this, and is instead recommended to format files when saving.

#### Format on save
- for the current project (recommended): Preferences > Editor > Code Style > Scala
- for all new projects: File > Other Settings > Preferences for New Projects… > Editor > Code Style > Scala

![IMAGE](/repository/assets/employee.png?raw=true "IMAGE")

#### Resume using IntelliJ formatter
To reset the formatter to IntelliJ for an existing project that uses the Scalafmt formatter:

- Open Preferences > Editor > Code Style > Scala
- Switch "Formatter" value to "IntelliJ"

It is not possible to reset this setting for all existing projects.

#### SBT

NB: keep in mind that versions of scalafmt-core and sbt-scalafmt are released independently, their versions do not align. The version of scalafmt-core is defined in the .scalafmt.conf configuration file and downloaded dynamically.

```
// In project/plugins.sbt. Note, does not support sbt 0.13, only sbt 1.x.
addSbtPlugin("org.scalameta" % "sbt-scalafmt" % SBT_PLUGIN_VERSION)
```

Latest published version of the sbt plugin:Maven Central

To configure the scalafmt version add the following line into .scalafmt.conf:

`version = 3.7.2`