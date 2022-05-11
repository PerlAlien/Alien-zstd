# NAME

Alien::zstd - Find or build zstd

# SYNOPSIS

From [ExtUtils::MakeMaker](https://metacpan.org/pod/ExtUtils%3A%3AMakeMaker):

    use ExtUtils::MakeMaker;
    use Alien::Base::Wrapper ();

    WriteMakefile(
      Alien::Base::Wrapper->new('Alien::zstd')->mm_args2(
        NAME => 'FOO::XS',
        ...
      ),
    );

From [Module::Build](https://metacpan.org/pod/Module%3A%3ABuild):

    use Module::Build;
    use Alien::Base::Wrapper qw( Alien::zstd !export );
    use Alien::zstd;

    my $build = Module::Build->new(
      ...
      configure_requires => {
        'Alien::Base::Wrapper' => '0',
        'Alien::zstd' => '0',
        ...
      },
      Alien::Base::Wrapper->mb_args,
      ...
    );

    $build->create_build_script;

From [Inline::C](https://metacpan.org/pod/Inline%3A%3AC) / [Inline::CPP](https://metacpan.org/pod/Inline%3A%3ACPP) script:

    use Inline 0.56 with => 'Alien::zstd';

From [Dist::Zilla](https://metacpan.org/pod/Dist%3A%3AZilla)

    [@Filter]
    -bundle = @Basic
    -remove = MakeMaker

    [Prereqs / ConfigureRequires]
    Alien::zstd = 0

    [MakeMaker::Awesome]
    header = use Alien::Base::Wrapper qw( Alien::zstd !export );
    WriteMakefile_arg = Alien::Base::Wrapper->mm_args

From [FFI::Platypus](https://metacpan.org/pod/FFI%3A%3APlatypus):

    use FFI::Platypus;
    use Alien::zstd;

    my $ffi = FFI::Platypus->new(
      lib => [ Alien::zstd->dynamic_libs ],
    );

Command line tool:

    use Alien::zstd;
    use Env qw( @PATH );

    unshift @PATH, Alien::zstd->bin_dir;

# DESCRIPTION

This distribution provides zstd so that it can be used by other
Perl distributions that are on CPAN.  It does this by first trying to
detect an existing install of zstd on your system.  If found it
will use that.  If it cannot be found, the source code will be downloaded
from the internet and it will be installed in a private share location
for the use of other modules.

# SEE ALSO

- [zstd](https://facebook.github.io/zstd/)

    The zstd home page.

- [Alien](https://metacpan.org/pod/Alien)

    Documentation on the Alien concept itself.

- [Alien::Base](https://metacpan.org/pod/Alien%3A%3ABase)

    The base class for this Alien.

- [Alien::Build::Manual::AlienUser](https://metacpan.org/pod/Alien%3A%3ABuild%3A%3AManual%3A%3AAlienUser)

    Detailed manual for users of Alien classes.
