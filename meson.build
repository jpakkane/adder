project('adder', 'c', 'rust', version: '1.0.0')

thread_dep = dependency('threads')
dl_dep = meson.get_compiler('c').find_library('dl', required: false)
m_dep = meson.get_compiler('c').find_library('m', required: false)

rl = static_library('radder', 'adder.rs', rust_crate_type: 'staticlib')

l = shared_library('adder', 'adder.c',
    c_args: '-DBUILDING_ADDER',
    link_with: rl,
    version: '1.0.0',
    soversion: '1',
    install: true,
    link_args: '-Wl,-u,adder_add', # Ensure that Rust code is not removed as unused.
    dependencies: [thread_dep, dl_dep, m_dep])
install_headers('adder.h')
test('adder', executable('addertest', 'addertest.c', link_with: l))
