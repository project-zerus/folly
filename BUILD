licenses(['notice'])

genrule(
  name = 'generate_escape_tables',
  srcs = [
    'folly/build/generate_escape_tables.py',
  ],
  outs = [
    'EscapeTables.cpp',
  ],
  cmd = '$(location folly/build/generate_escape_tables.py) --install_dir=$(@D)'
)

genrule(
  name = 'generate_format_tables',
  srcs = [
    'folly/build/generate_format_tables.py',
  ],
  outs = [
    'FormatTables.cpp',
  ],
  cmd = '$(location folly/build/generate_format_tables.py) --install_dir=$(@D)'
)

genrule(
  name = 'generate_varint_tables',
  srcs = [
    'folly/build/generate_varint_tables.py',
  ],
  outs = [
    'GroupVarintTables.cpp',
  ],
  cmd = '$(location folly/build/generate_varint_tables.py) --install_dir=$(@D)'
)

cc_library(
  name = 'base',
  deps = [
    '//external:boost',
    '//external:double-conversion',
    '//external:glog',
  ],
  hdrs = [
  ],
  srcs = [
    ':generate_escape_tables',
    ':generate_format_tables',
    ':generate_varint_tables',
    'folly/Conv.cpp',
    'folly/Demangle.cpp',
    'folly/Format.cpp',
    'folly/Malloc.cpp',
    'folly/Range.cpp',
    'folly/String.cpp',
    'folly/Unicode.cpp',
  ],
  includes = [
    '.',
    '__build__/linux',
  ],
  copts = [
    '-std=c++11',
  ],
)

cc_binary(
  name = 'generate_fingerprint_tables_exe',
  deps = [
    ':base',
  ],
  srcs = [
    'folly/build/GenerateFingerprintTables.cpp',
  ],
)

genrule(
  name = 'generate_fingerprint_tables',
  srcs = [
  ],
  outs = [
    'FingerprintTables.cpp',
  ],
  cmd = 'generate_fingerprint_tables_exe -install_dir=$(@D)',
  tools = [
    ':generate_fingerprint_tables_exe',
  ]
)

cc_library(
  name = 'folly',
  visibility = ['//visibility:public'],
  deps = [
    ':base',
    '//external:libssl',
  ],
  hdrs = [
  ],
  srcs = [
    ':generate_fingerprint_tables',
    'folly/Bits.cpp',
    'folly/detail/CacheLocality.cpp',
    'folly/dynamic.cpp',
    'folly/File.cpp',
    'folly/FileUtil.cpp',
    'folly/futures/detail/ThreadWheelTimekeeper.cpp',
    'folly/futures/Future.cpp',
    'folly/futures/InlineExecutor.cpp',
    'folly/futures/ManualExecutor.cpp',
    'folly/futures/QueuedImmediateExecutor.cpp',
    'folly/detail/Futex.cpp',
    'folly/GroupVarint.cpp',
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
    'folly/io/async/Request.cpp',
    'folly/io/async/SSLContext.cpp',
    'folly/io/async/HHWheelTimer.cpp',
    'folly/io/async/test/TimeUtil.cpp',
    'folly/json.cpp',
    'folly/detail/MemoryIdler.cpp',
    'folly/MacAddress.cpp',
    'folly/MemoryMapping.cpp',
    'folly/Random.cpp',
    'folly/SafeAssert.cpp',
    'folly/SocketAddress.cpp',
    'folly/Singleton.cpp',
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
    'folly/experimental/fibers/TimeoutController.cpp',
    'folly/experimental/FunctionScheduler.cpp',
    'folly/experimental/io/FsUtil.cpp',
    'folly/experimental/io/HugePages.cpp',
    'folly/experimental/JSONSchema.cpp',
    'folly/experimental/Select64.cpp',
    'folly/experimental/SharedMutex.cpp',
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
  copts = [
    '-std=c++11',
  ],
)
