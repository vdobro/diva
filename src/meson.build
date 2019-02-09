diva_sources = [
  'auto_type_registration.vala',
  'collection_dependencies.vala',
  'container_builder.vala',
  'creation_strategy.vala',
  'creator_index.vala',
  'default_container.vala',
  'delegate_registration.vala',
  'indexed_dependencies.vala',
  'instance_registration.vala',
  'i_registration_context.vala',
  'lazy_dependencies.vala',
  'resolve_error.vala',
]

diva_deps = [
  dependency('glib-2.0'),
  dependency('gobject-2.0'),
  dependency('gee-0.8'),
]

diva_include = include_directories('.')

lib_version = '0.1'
gir_file = 'Diva-' + lib_version + '.gir'

diva_lib = library('diva', diva_sources,
  dependencies: diva_deps,
  vala_gir: gir_file,
  install: true,
  install_dir: [true, true, true, true],
)

pkg = import('pkgconfig')
pkg.generate(diva_lib,
  description: 'Dependency injection library for vala/glib',
  install_dir: join_paths(get_option('libdir'), 'pkgconfig'),
)

diva_dep = declare_dependency(include_directories : diva_include,
  link_with : diva_lib)

g_ir_compiler = find_program('g-ir-compiler')
custom_target('diva typelib',
  command: [
    g_ir_compiler,
    '--shared-library', diva_lib.full_path(),
    '--output', '@OUTPUT@',
    join_paths(meson.current_build_dir(), gir_file)
  ],
  output: 'Diva-' + lib_version + '.typelib',
  depends: diva_lib,
  install: true,
  install_dir: join_paths(get_option('libdir'), 'girepository-1.0'),
)
