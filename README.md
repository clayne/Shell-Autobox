# Shell::Autobox

[![Build Status](https://travis-ci.org/chocolateboy/Shell-Autobox.svg)](https://travis-ci.org/chocolateboy/Shell-Autobox)
[![CPAN Version](https://badge.fury.io/pl/Shell-Autobox.svg)](https://badge.fury.io/pl/Shell-Autobox)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [NAME](#name)
- [SYNOPSIS](#synopsis)
- [DESCRIPTION](#description)
- [EXPORT](#export)
- [VERSION](#version)
- [SEE ALSO](#see-also)
- [AUTHOR](#author)
- [COPYRIGHT AND LICENSE](#copyright-and-license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# NAME

Shell::Autobox - pipe Perl strings through shell commands

# SYNOPSIS

```perl
use Shell::Autobox qw(xmllint);

my $xml = '<foo bar="baz"><bar /><baz /></foo>';
my $pretty = $xml->xmllint('--format -');
```

# DESCRIPTION

Shell::Autobox provides an easy way to pipe Perl strings through shell commands. Commands passed as arguments to the
`use Shell::Autobox` statement are installed as subroutines in the calling package, and that package is then
registered as the handler for methods called on ordinary (i.e. non-reference) scalars.

When a method corresponding to a registered command is called on a scalar, the scalar is passed as the command's standard input;
additional arguments are passed through as a space-delimited list of options, and - if no error occurs - the
command's standard output is returned. This can then be piped into other commands.

The registered methods can also be called as regular functions e.g.

```perl
use Shell::Autobox qw(cut);

my $bar = cut("foo:bar:baz", "-d':' -f2");
```

# EXPORT

None by default.

# VERSION

0.40.0

# SEE ALSO

* [autobox](https://metacpan.org/pod/autobox)
* [autobox::Core](https://metacpan.org/pod/autobox::Core)
* [Shell](https://metacpan.org/pod/Shell)

# AUTHOR

[chocolateboy](mailto:chocolate@cpan.org)

# COPYRIGHT AND LICENSE

Copyright © 2003-2020 by chocolateboy.

This is free software; you can redistribute it and/or modify it under the terms of the
[Artistic License 2.0](https://www.opensource.org/licenses/artistic-license-2.0.php).
