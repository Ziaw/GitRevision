GitVersion - nemerle macro for automate .net assembly version number.
=====================================================================

##  Usage

Replace AssemblyVersion attribute with AssemblyVersionFromGit("GitTag.0.GitRev") macro.

Macro runs "git describe --tags --long" and parse output like "v1.1-42-g23a4f75".
    'GitTag' string replaced with 1.1
    'GitRev' string replaced with 42
  
Assembly version will be "1.1.0.42".
  