gen_rule(
  name = 'escape_tables',
  srcs = [
    'folly/build/generate_escape_tables.py'
  ],
  outs = [
    'EscapeTables.cpp',
  ],
  cmd = '$FIRST_SRC --install_dir=$BUILD_DIR/folly'
)

gen_rule(
  name = 'format_tables',
  srcs = [
    'folly/build/generate_format_tables.py'
  ],
  outs = [
    'FormatTables.cpp',
  ],
  cmd = '$FIRST_SRC --install_dir=$BUILD_DIR/folly'
)

gen_rule(
  name = 'varint_tables',
  srcs = [
    'folly/build/generate_varint_tables.py'
  ],
  outs = [
    'GroupVarintTables.cpp',
  ],
  cmd = '$FIRST_SRC --install_dir=$BUILD_DIR/folly'
)

cc_binary(
  name = 'generate_fingerprint_tables',
  warning = 'no',
  srcs = [
    'folly/build/GenerateFingerprintTables.cpp'
  ],
  deps = [
    ':follybase',
    '//boost:boost',
    '//thirdparty/glog:glog',
  ],
)

gen_rule(
  name = 'fingerfrint_tables',
  outs = [
    'FingerprintTables.cpp',
  ],
  cmd = 'blade-bin/folly/generate_fingerprint_tables --install_dir=$BUILD_DIR/folly',
  deps = [
    ':generate_fingerprint_tables',
  ]
)

cc_library(
  name = 'follybase',
  warning = 'no',
  export_incs = [
    '.'
  ],
  srcs = [
    'folly/Conv.cpp',
    'folly/Demangle.cpp',
    'EscapeTables.cpp',
    'folly/Format.cpp',
    'FormatTables.cpp',
    'folly/Malloc.cpp',
    'folly/Range.cpp',
    'folly/StringBase.cpp',
    'folly/String.cpp',
    'folly/Unicode.cpp',
  ],
  deps = [
    ':escape_tables',
    ':format_tables',
    '//boost:boost',
    '//double-conversion:double-conversion',
    '//thirdparty/glog:glog',
  ]
)

cc_library(
  name = 'folly',
  warning = 'no',
  srcs = [
    'folly/Bits.cpp',
    'folly/detail/CacheLocality.cpp',
    'folly/dynamic.cpp',
    'folly/File.cpp',
    'folly/FileUtil.cpp',
    'FingerprintTables.cpp',
    'folly/futures/detail/ThreadWheelTimekeeper.cpp',
    'folly/futures/Future.cpp',
    'folly/futures/InlineExecutor.cpp',
    'folly/futures/ManualExecutor.cpp',
    'folly/futures/QueuedImmediateExecutor.cpp',
    'folly/detail/Futex.cpp',
    'folly/GroupVarint.cpp',
    'GroupVarintTables.cpp',
    'folly/IPAddress.cpp',
    'folly/IPAddressV4.cpp',
    'folly/IPAddressV6.cpp',
    'folly/LifoSem.cpp',
    'folly/io/Compression.cpp',
    'folly/io/IOBuf.cpp',
    'folly/io/IOBufQueue.cpp',
    'folly/io/RecordIO.cpp',
    'folly/io/ShutdownSocketSet.cpp',
    'folly/io/async/AsyncTimeout.cpp',
    'folly/io/async/AsyncUDPSocket.cpp',
    'folly/io/async/AsyncServerSocket.cpp',
    'folly/io/async/AsyncSignalHandler.cpp',
    'folly/io/async/AsyncSocket.cpp',
    'folly/io/async/AsyncSSLSocket.cpp',
    'folly/io/async/EventBase.cpp',
    'folly/io/async/EventBaseManager.cpp',
    'folly/io/async/EventHandler.cpp',
    'folly/io/async/SSLContext.cpp',
    'folly/io/async/HHWheelTimer.cpp',
    'folly/io/async/test/TimeUtil.cpp',
    'folly/json.cpp',
    'folly/detail/MemoryIdler.cpp',
    'folly/MacAddress.cpp',
    'folly/MemoryMapping.cpp',
    'folly/Random.cpp',
    'folly/SafeAssert.cpp',
    'folly/SharedMutex.cpp',
    'folly/Singleton.cpp',
    'folly/SocketAddress.cpp',
    'folly/SpookyHashV1.cpp',
    'folly/SpookyHashV2.cpp',
    'folly/stats/Instantiations.cpp',
    'folly/Subprocess.cpp',
    'folly/ThreadCachedArena.cpp',
    'folly/TimeoutQueue.cpp',
    'folly/Uri.cpp',
    'folly/Version.cpp',
    'folly/experimental/fibers/Baton.cpp',
    'folly/experimental/fibers/Fiber.cpp',
    'folly/experimental/fibers/FiberManager.cpp',
    'folly/experimental/fibers/FiberManagerMap.cpp',
    'folly/experimental/fibers/GuardPageAllocator.cpp',
    'folly/experimental/fibers/TimeoutController.cpp',
    'folly/experimental/FunctionScheduler.cpp',
    'folly/experimental/io/FsUtil.cpp',
    'folly/experimental/io/HugePages.cpp',
    'folly/experimental/JSONSchema.cpp',
    'folly/experimental/Select64.cpp',
    'folly/experimental/TestUtil.cpp',
    'folly/wangle/acceptor/Acceptor.cpp',
    'folly/wangle/acceptor/ConnectionManager.cpp',
    'folly/wangle/acceptor/LoadShedConfiguration.cpp',
    'folly/wangle/acceptor/ManagedConnection.cpp',
    'folly/wangle/acceptor/SocketOptions.cpp',
    'folly/wangle/acceptor/TransportInfo.cpp',
    'folly/wangle/bootstrap/ServerBootstrap.cpp',
    'folly/wangle/concurrent/CPUThreadPoolExecutor.cpp',
    'folly/wangle/concurrent/Codel.cpp',
    'folly/wangle/concurrent/IOThreadPoolExecutor.cpp',
    'folly/wangle/concurrent/GlobalExecutor.cpp',
    'folly/wangle/concurrent/ThreadPoolExecutor.cpp',
    'folly/wangle/ssl/PasswordInFile.cpp',
    'folly/wangle/ssl/SSLContextManager.cpp',
    'folly/wangle/ssl/SSLSessionCacheManager.cpp',
    'folly/wangle/ssl/SSLUtil.cpp',
    'folly/wangle/ssl/TLSTicketKeyManager.cpp',
  ],
  deps = [
    ':follybase',
    ':fingerfrint_tables',
    ':varint_tables',
    '//libevent:libevent',
    '//lz4/lib:lz4',
    '//openssl:openssl',
    '//snappy:snappy',
  ]
)
