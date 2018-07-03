project('TemporalSoften2', 'c',
        version: '1',
        default_options: ['cpp_std=c99', 'buildtype=release'],
        meson_version: '>=0.46')


warnings = [
  '-Wall',
  '-Wextra',
  '-Wshadow',
]

cflags = [
  warnings,
  '-DTEMPORALSOFTEN2_VERSION="@0@"'.format(meson.project_version()),
]

ldflags = [
]


host_cpu_family = host_machine.cpu_family()

if host_cpu_family.startswith('x86')
  cflags += ['-mfpmath=sse', '-msse2']
else
  error('Currently only x86 systems are supported.')
endif


host_system = host_machine.system()

if host_system == 'windows' or host_system == 'cygwin'
  if host_cpu_family == 'x86'
    cflags += '-mstackrealign'
    ldflags += '-Wl,--kill-at'
  endif
endif


cc = meson.get_compiler('c')


sources = [
  'src/temporalsoften2.c',
]

deps = [
  dependency('vapoursynth').partial_dependency(includes: true, compile_args: true),
  cc.find_library('m', required: false),
]

shared_module('temporalsoften2',
              sources,
              dependencies: deps,
              link_args: ldflags,
              c_args: cflags,
              install: true)
