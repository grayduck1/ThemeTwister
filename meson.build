project(
    'themetwister',
    'vala', 'c',
    version: '0.0.1',
    meson_version: '>=0.45.0'
)

PROJECT_NAME = 'themetwister'
prefix = get_option('prefix')
libdir = join_paths(prefix, get_option('libdir'))
datadir = join_paths(prefix, get_option('datadir'))

VAPI_DIR = join_paths(meson.source_root(), 'vapi')
vala = meson.get_compiler('vala')

conf = configuration_data()
conf.set_quoted('PROJECT_NAME', PROJECT_NAME)
conf.set_quoted('PACKAGE_LIBDIR', libdir)
conf.set_quoted('PACKAGE_SHAREDIR', datadir)

config_h = configure_file(
	output: 'config.h',
	configuration: conf
)

config_dep = declare_dependency(
	dependencies: vala.find_library('config', dirs: VAPI_DIR),
	sources: config_h
)

config_inc_dir = include_directories('.')

OnBoardingValaArgs = [
    '--pkg=config',
    '--vapidir=' + VAPI_DIR,
    '--target-glib=2.38',
]

# Create a new executable, list the files we want to compile, list the dependencies we need, and install
executable(
    meson.project_name(),
    'src/Application.vala',
    'src/Page/Welcome.vala',
    'src/Page/TwisterOS.vala',
    'src/Page/Twister95.vala',
    'src/Page/TwisterXP.vala',
    'src/Page/Twister7.vala',
    'src/Page/Twister10.vala',
    'src/Page/Twister11.vala',
    'src/Page/iTwister.vala',
    'src/Page/iTwisterSur.vala',
    'src/Page/TwisterPlasma.vala',
    dependencies: [
        dependency('gtk+-3.0', version: '>=3.22'),
        dependency('cairo', version: '>=1.15.0'),
        meson.get_compiler('c').find_library('m', required: false)
    ],
    c_args: [
        '-DGMENU_I_KNOW_THIS_IS_UNSTABLE',
    ],
    vala_args: OnBoardingValaArgs,
    include_directories: config_inc_dir,
    install: true
)

# Install CSS file
install_data(
    join_paths('data', 'themetwister.css'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)

install_data(
    join_paths('data', 'themetwister_dark.css'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)

# Install images
install_data(
    join_paths('data', 'iRaspbian.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'iRaspbianSur.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'Raspbian7.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'Raspbian95.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'RaspbianX.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'RaspbianXP.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'TwisterOS.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'Twister11.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
install_data(
    join_paths('data', 'TwisterPlasma.png'),
    install_dir: join_paths(datadir, PROJECT_NAME)
)
