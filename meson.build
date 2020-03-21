project('amdgpuinfo', 'c',
        version: '0.1',
        meson_version: '>= 0.45.1',
        default_options : [
          'c_std=c11',
          'warning_level=3',
        ],
)

project_args = [
  '-D_GNU_SOURCE' # For strdup in C11
]

pci_dep = dependency('libpci')
hwloc_dep = dependency('hwloc', required: false)
opencl_dep = dependency('OpenCL', required: false)

if (hwloc_dep.found() and opencl_dep.found())
  project_args += ['-DUSE_OPENCL']
endif

add_project_arguments(project_args, language: ['c'])

executable(
  'amdgpuinfo', ['amdgpuinfo.c'],
  dependencies: [pci_dep, hwloc_dep, opencl_dep],
  install: true)
