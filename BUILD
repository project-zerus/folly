cc_library(
  name = 'folly',
  deps = [
    './folly:folly'
  ]
)

cc_library(
  name = 'headers',
  export_incs = '.',
  deps = [
    '#pthread',
    '//boost:boost',
    '//double-conversion:double-conversion',
    '//snappy:snappy',
    '//thirdparty/gflags:gflags',
    '//thirdparty/glog:glog',
    '//thirdparty/libevent:libevent',
    '//zlib:zlib',
  ]
)
