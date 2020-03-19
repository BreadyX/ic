project('ic',
        version: '2.0.0')

python = import('python')

python_install = python.find_installation('python3')
lang_ver = python_install.language_version()

assert(lang_ver.version_compare('>=3.6'), 'Python ' + lang_ver + ' is too old')

conf_data = configuration_data()
conf_data.set('name', meson.project_name())
conf_data.set('version', meson.project_version())
conf_data.set('default_compiler_cmd', 'gcc -x c -o {1} {0}')
ic = configure_file(input:  'ic.in',
                    output: 'ic',
                    configuration: conf_data)

install_data(ic, install_dir: './bin', install_mode: 'rwxr-xr-x')

