GeneratedAssemblyVersion - nemerle macro for automate .net assembly version number.
===================================================================================

##  Usage

Replace AssemblyVersion attribute with GeneratedAssemblyVersion macro.

Example:

```nemerle
[assembly: GeneratedAssemblyVersion("$Major.$Minor.$BUILD_NUMBER.0", Defaults(Major="3", Minor="5", BUILD_NUMBER="0"))]
```

Macro search environment variables Major and Minor and insert them values into assembly version attribute. If Major and Minor not found - use default values. If default vaues is not set comilation error occures.
E.g. BUILD_NUMBER can be set by CI server during build and you do not need build time source file generators.

## Git special variables

Macro have two special variables: GitTag and GitRev. If not found in environment, macro trying to evaluate them from git repostitory which contains source.

Example:

```nemerle
[assembly: GeneratedAssemblyVersion("GitTag.0.GitRevision", Defaults(GitTag="3.0", GitRevision="9999"))]
```

Unless GitTag or GitRev environment defined, macro runs "git describe --tags --long" and parse output like "v1.1-42-g23a4f75".
    'GitTag' string replaced with 1.1 (digits and dots characters only of the last tag)
    'GitRev' string replaced with 42 (revisions count since last tag)
  
Assembly version will be "1.1.0.42".

