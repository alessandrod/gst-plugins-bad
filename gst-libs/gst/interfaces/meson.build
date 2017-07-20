photography_sources = ['photography.c']
photo_headers = ['photography.h']
install_headers(photo_headers, subdir : 'gstreamer-1.0/gst/interfaces')

photo_enums = gnome.mkenums_simple('photography-enumtypes',
  sources : photo_headers,
  header_prefix : '#include <gst/gst.h>',
  decorator: 'GST_EXPORT',
  install_header: true,
  install_dir : 'include/gstreamer-1.0/gst/interfaces/')
photoenum_c = photo_enums[0]
photoenum_h = photo_enums[1]

gstphotography = library('gstphotography-' + api_version,
  photography_sources, photoenum_h, photoenum_c,
  c_args : gst_plugins_bad_args + ['-DGST_USE_UNSTABLE_API'],
  include_directories : [configinc, libsinc],
  version : libversion,
  soversion : soversion,
  install : true,
  dependencies : [gst_dep],
  vs_module_defs: vs_module_defs_dir + 'libgstphotography.def',
)

gstphotography_dep = declare_dependency(link_with : gstphotography,
  include_directories : [libsinc],
  dependencies : [gst_dep],
  sources : [photoenum_h])
