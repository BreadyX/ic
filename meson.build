project('ic',
        version: '1.99.0-dev')

python = import('python')

python_install = python.find_installation('python3')

conf_data = configuration_data()
conf_data.set('name', meson.project_name())
conf_data.set('version', meson.project_version())
ic = configure_file(input:  'ic.in',
                    output: 'ic',
                    configuration: conf_data)

install_data(ic, install_dir: './bin', install_mode: 'rwxr-xr-x')

