AC_INIT( [mkimage-profile-live], [0.1] )

BASEDIR=`realpath .`
SQUASHFS_COMPRESSION=xz

AC_ARG_WITH(aptconf,
	AC_HELP_STRING([--with-aptconf=file], [custom apt.conf location, e.g '--with-aptconf=/etc/apt/apt.conf']),
	[
		AC_MSG_CHECKING([apt.conf file])
		if test -r "$with_aptconf"  ; then
			APTCONF="$with_aptconf"
			AC_MSG_RESULT(["$with_aptconf exists"])
		fi
	],
	[
		APTCONF=/etc/apt/apt.conf
	])

AC_ARG_WITH(sources,
	AC_HELP_STRING([--with-sources=file], [custom sources.list location, e.g '--with-sources=./sources.list.x86_64']),
	[
		AC_MSG_CHECKING([sources.list file])
		if test -r "$with_sources"; then
			APTCONF=`realpath .`/apt.conf
			SOURCES_LIST=`realpath "$with_sources"`
			AC_MSG_RESULT(["$with_sources exists"])
		fi
	],
	[
		SOURCES_LIST=`realpath .`/sources.list
	])

AC_ARG_WITH(release,
	AC_HELP_STRING([--with-release=release], [install altlinux-release-* package]),
	[
		AC_MSG_CHECKING([release])
		RELEASE="$with_release"
	],
	[
		RELEASE=sisyphus
	])

AC_ARG_WITH(kernel,
	AC_HELP_STRING([--with-kernel=kernel], [install kernel-image-* package]),
	[
		AC_MSG_CHECKING([kernel])
		if test "$with_kernel" = "ovz-el"; then
			SQUASHFS_COMPRESSION=gzip
		fi
		KERNEL="$with_kernel"
	],
	[
		KERNEL=std-def
	])

AC_ARG_WITH(user,
	AC_HELP_STRING([--with-user=user], [user : default user name]),
	[
		AC_MSG_CHECKING([user])
		USER="$with_user"
	],
	[
		USER="altlive"
	])

AC_ARG_WITH(locale,
	AC_HELP_STRING([--with-locale=locale], [locale : en_US, ru_RU, ...]),
	[
		AC_MSG_CHECKING([locale])
		LOCALE="$with_locale"
	],
	[
		LOCALE="en_US"
	])

AC_ARG_WITH(timezone,
	AC_HELP_STRING([--with-timezone=timezone], [timezone : Europe/London, Europe/Moscow, ...]),
	[
		AC_MSG_CHECKING([timezone])
		TIMEZONE="$with_timezone"
	],
	[
		TIMEZONE="Europe/Kiev"
	])

AC_ARG_WITH(outdir,
	AC_HELP_STRING([--with-outdir=dir],
    [custom output files location, e.g '--with-outdir=/home/user/out/']),
    [
    	AC_MSG_CHECKING([outdir])
        if test -d "$with_outdir"; then
        	OUTDIR="$with_outdir"
            AC_MSG_RESULT(["$with_outdir exists"])
        fi
    ],
    [
    	OUTDIR=`pwd`/profiles/out
    ])

AC_SUBST(BASEDIR)
AC_SUBST(APTCONF)
AC_SUBST(SOURCES_LIST)
AC_SUBST(RELEASE)
AC_SUBST(KERNEL)
AC_SUBST(FEATURES)
AC_SUBST(USER)
AC_SUBST(LOCALE)
AC_SUBST(TIMEZONE)
AC_SUBST(OUTDIR)
AC_SUBST(SQUASHFS_COMPRESSION)

AC_CONFIG_FILES([
	Makefile
	apt.conf
	boot/options.mk
	live/Makefile
	live/packages.d/kernel.lst
])

AC_OUTPUT
