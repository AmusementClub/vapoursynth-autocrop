project('autocrop', 'cpp',
  default_options: ['buildtype=release', 'warning_level=2', 'b_lto=true', 'b_ndebug=if-release', 'cpp_std=c++11'],
  meson_version: '>=0.51.0',
  version: '1'
)

cxx = meson.get_compiler('cpp')

gcc_syntax = cxx.get_argument_syntax() == 'gcc'

if gcc_syntax
  vapoursynth_dep = dependency('vapoursynth').partial_dependency(compile_args: true, includes: true)
  install_dir = vapoursynth_dep.get_variable(pkgconfig: 'libdir') / 'vapoursynth'
else
  vapoursynth_dep = []
  install_dir = get_option('libdir') / 'vapoursynth'
endif

sources = [
  'autocrop.cpp'
]

shared_module('autocrop', sources,
  dependencies: vapoursynth_dep,
  install: true,
  install_dir: install_dir,
  gnu_symbol_visibility: 'hidden'
)
