srtp_sources = [
  'gstsrtp.c',
  'gstsrtpdec.c',
  'gstsrtpenc.c',
]

srtp_dep = dependency('libsrtp', required : false)
if not srtp_dep.found() and cc.has_header_symbol('srtp/srtp.h', 'srtp_init')
  srtp_dep = cc.find_library('srtp', required : false)
endif

if srtp_dep.found()
  gstsrtp_enums = gnome.mkenums_simple('gstsrtp-enumtypes',
    sources : ['gstsrtp.h'],
    install_header: false)

  gstsrtp = library('gstsrtp',
    srtp_sources, gstsrtp_enums,
    c_args : gst_plugins_bad_args,
    link_args : noseh_link_args,
    include_directories : [configinc],
    dependencies : [gstrtp_dep, gstvideo_dep, srtp_dep],
    install : true,
    install_dir : plugins_install_dir,
  )
endif
