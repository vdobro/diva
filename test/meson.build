test_sources = [
  'collection_tests.vala',
  'creation_strategy_tests.vala',
  'decorator_tests.vala',
  'error_tests.vala',
  'index_tests.vala',
  'lazy_tests.vala',
  'module_tests.vala',
  'property_tests.vala',
  'registration_errors.vala',
  'test_fixture.vala',
  'test_main.vala',
]

test_deps = [
  dependency('gee-0.8')
]

e = executable('diva_test', test_sources,
  link_with: diva_lib,
  dependencies: test_deps,
  include_directories: diva_include,
)
test('diva test', e)