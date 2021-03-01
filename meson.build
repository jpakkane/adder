project('adder', 'c', version: '1.0.0')

l = shared_library('adder', 'adder.c',
    version: '1.0.0',
    soversion: '1',
    install: true)
install_headers('adder.h')
test('adder', executable('addertest', 'addertest.c', link_with: l))
