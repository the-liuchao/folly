SUBDIRS = . function_benchmark

ACLOCAL_AMFLAGS = -I m4

CPPFLAGS += -Igtest-1.7.0/include

TESTS= \
	sorted_vector_types_test \
	foreach_test \
	hash_test \
	timeout_queue_test \
	conv_test \
	range_test \
	bits_test \
	bit_iterator_test

check_LTLIBRARIES = libfollytestmain.la libgtest.la
check_PROGRAMS =

libgtest_la_CPPFLAGS = -Igtest-1.7.0 -Igtest-1.7.0/src
libgtest_la_SOURCES = gtest-1.7.0/src/gtest-all.cc

if FOLLY_TESTMAIN
libfollytestmain_la_CPPFLAGS = $(AM_CPPFLAGS) $(libgtest_la_CPPFLAGS)
libfollytestmain_la_SOURCES = $(libgtest_la_SOURCES) common/TestMain.cpp
libfollytestmain_la_LIBADD = $(top_builddir)/init/libfollyinit.la $(top_builddir)/libfolly.la
else
libfollytestmain_la_CPPFLAGS = $(libgtest_la_CPPFLAGS)
libfollytestmain_la_SOURCES = $(libgtest_la_SOURCES) gtest-1.7.0/src/gtest_main.cc
libfollytestmain_la_LIBADD = $(top_builddir)/libfolly.la
endif

noinst_HEADERS = FBStringTestBenchmarks.cpp.h \
	FBVectorTestBenchmarks.cpp.h

spin_lock_test_SOURCES = SpinLockTest.cpp
spin_lock_test_LDADD = libfollytestmain.la
TESTS += spin_lock_test

if RUN_ARCH_SPECIFIC_TESTS
small_locks_test_SOURCES = SmallLocksTest.cpp
small_locks_test_LDADD = libfollytestmain.la
TESTS += small_locks_test

# Fails with WARNING: Logging before InitGoogleLogging() is written to STDERR
packed_sync_ptr_test_SOURCES = PackedSyncPtrTest.cpp
packed_sync_ptr_test_LDADD = libfollytestmain.la
TESTS += packed_sync_ptr_test

small_vector_test_SOURCES = small_vector_test.cpp
small_vector_test_LDADD = libfollytestmain.la
TESTS += small_vector_test

discriminated_ptr_test_SOURCES = DiscriminatedPtrTest.cpp
discriminated_ptr_test_LDADD = libfollytestmain.la
TESTS += discriminated_ptr_test

if !HAVE_PPC64
cpuid_test_SOURCES = CpuIdTest.cpp
cpuid_test_LDADD = libfollytestmain.la
TESTS += cpuid_test
endif
endif

sorted_vector_types_test_SOURCES = sorted_vector_test.cpp
sorted_vector_types_test_LDADD = libfollytestmain.la


foreach_test_SOURCES = ForeachTest.cpp
foreach_test_LDADD = libfollytestmain.la

foreach_benchmark_SOURCES = ForeachBenchmark.cpp
foreach_benchmark_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
check_PROGRAMS += foreach_benchmark

hash_test_SOURCES = HashTest.cpp
hash_test_LDADD = libfollytestmain.la


fbstring_test_using_jemalloc_SOURCES = FBStringTest.cpp
fbstring_test_using_jemalloc_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += fbstring_test_using_jemalloc

thread_cached_int_test_SOURCES = ThreadCachedIntTest.cpp
thread_cached_int_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la

thread_local_test_SOURCES = ThreadLocalTest.cpp
thread_local_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
thread_local_test_LDFLAGS = -ldl
TESTS += thread_cached_int_test thread_local_test

fbvector_test_SOURCES = FBVectorTest.cpp
fbvector_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += fbvector_test

# fails due to cout
dynamic_test_SOURCES = DynamicTest.cpp
dynamic_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += dynamic_test

# fails due to cout
json_test_SOURCES = JsonTest.cpp
json_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += json_test

benchmark_test_SOURCES = BenchmarkTest.cpp
benchmark_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
check_PROGRAMS += benchmark_test

# fails due to destructor
scope_guard_test_SOURCES = ScopeGuardTest.cpp
scope_guard_test_LDADD = libfollytestmain.la
TESTS += scope_guard_test

timeout_queue_test_SOURCES = TimeoutQueueTest.cpp
timeout_queue_test_LDADD = libfollytestmain.la

conv_test_SOURCES = ConvTest.cpp
conv_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la

range_test_SOURCES = RangeTest.cpp
range_test_LDADD = libfollytestmain.la

bits_test_SOURCES = BitsTest.cpp
bits_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la

bit_iterator_test_SOURCES = BitIteratorTest.cpp
bit_iterator_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la

endian_test_SOURCES = EndianTest.cpp
endian_test_LDADD = libfollytestmain.la
TESTS += endian_test

rw_spinlock_test_SOURCES = RWSpinLockTest.cpp
rw_spinlock_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += rw_spinlock_test

synchronized_test_SOURCES = SynchronizedTest.cpp
synchronized_test_LDADD = libfollytestmain.la
TESTS += synchronized_test

concurrent_skiplist_test_SOURCES = ConcurrentSkipListTest.cpp
concurrent_skiplist_test_LDADD = libfollytestmain.la
TESTS += concurrent_skiplist_test

concurrent_skiplist_benchmark_SOURCES = ConcurrentSkipListBenchmark.cpp
concurrent_skiplist_benchmark_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
check_PROGRAMS += concurrent_skiplist_benchmark

histogram_test_SOURCES = HistogramTest.cpp
histogram_test_LDADD = libfollytestmain.la
TESTS += histogram_test

group_varint_test_SOURCES = GroupVarintTest.cpp
group_varint_test_LDADD = libfollytestmain.la
TESTS += group_varint_test

map_util_test_SOURCES = MapUtilTest.cpp
map_util_test_LDADD = libfollytestmain.la
TESTS += map_util_test

string_test_SOURCES = StringTest.cpp
string_test_LDADD = libfollytestmain.la
TESTS += string_test

conditionally_existent_test_SOURCES = ConditionallyExistentTest.cpp
conditionally_existent_test_LDADD = libfollytestmain.la
TESTS += conditionally_existent_test

producer_consumer_queue_test_SOURCES = ProducerConsumerQueueTest.cpp
producer_consumer_queue_test_LDADD = libfollytestmain.la
TESTS += producer_consumer_queue_test

atomic_hash_array_test_SOURCES = AtomicHashArrayTest.cpp
atomic_hash_array_test_LDADD = libfollytestmain.la
TESTS += atomic_hash_array_test

atomic_hash_map_test_SOURCES = AtomicHashMapTest.cpp
atomic_hash_map_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += atomic_hash_map_test

format_test_SOURCES = FormatTest.cpp
format_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += format_test

fingerprint_test_SOURCES = FingerprintTest.cpp
fingerprint_test_LDADD = libfollytestmain.la $(top_builddir)/libfollybenchmark.la
TESTS += fingerprint_test

portability_test_SOURCES = PortabilityTest.cpp
portability_test_LDADD = libfollytestmain.la
TESTS += portability_test

spooky_hash_v1_test_SOURCES = SpookyHashV1Test.cpp
spooky_hash_v1_test_LDADD = libfollytestmain.la  $(top_builddir)/libfollybenchmark.la
TESTS += spooky_hash_v1_test

spooky_hash_v2_test_SOURCES = SpookyHashV2Test.cpp
spooky_hash_v2_test_LDADD = libfollytestmain.la  $(top_builddir)/libfollybenchmark.la
TESTS += spooky_hash_v2_test

token_bucket_test_SOURCES = TokenBucketTest.cpp
token_bucket_test_LDADD = libfollytestmain.la  $(top_builddir)/libfollybenchmark.la
TESTS += token_bucket_test

thread_name_test_SOURCES = ThreadNameTest.cpp
thread_name_test_LDADD = libfollytestmain.la
TESTS += thread_name_test

indestructible_test_SOURCES = IndestructibleTest.cpp
indestructible_test_LDADD = libfollytestmain.la
TESTS += indestructible_test


futures_test_SOURCES = \
    ../futures/test/CollectTest.cpp \
    ../futures/test/ContextTest.cpp \
    ../futures/test/ConversionTest.cpp \
    ../futures/test/CoreTest.cpp \
    ../futures/test/ThreadedExecutorTest.cpp \
    ../futures/test/EnsureTest.cpp \
    ../futures/test/ExecutorTest.cpp \
    ../futures/test/FSMTest.cpp \
    ../futures/test/FilterTest.cpp \
    ../futures/test/FutureTest.cpp \
    ../futures/test/HeaderCompileTest.cpp \
    ../futures/test/InterruptTest.cpp \
    ../futures/test/MapTest.cpp \
    ../futures/test/PollTest.cpp \
    ../futures/test/PromiseTest.cpp \
    ../futures/test/ReduceTest.cpp \
    ../futures/test/RetryingTest.cpp \
    ../futures/test/SelfDestructTest.cpp \
    ../futures/test/SharedPromiseTest.cpp \
    ../futures/test/ThenCompileTest.cpp \
    ../futures/test/ThenTest.cpp \
    ../futures/test/TimekeeperTest.cpp \
    ../futures/test/TimesTest.cpp \
    ../futures/test/TryTest.cpp \
    ../futures/test/UnitTest.cpp \
    ../futures/test/UnwrapTest.cpp \
    ../futures/test/ViaTest.cpp \
    ../futures/test/WaitTest.cpp \
    ../futures/test/WillEqualTest.cpp \
    ../futures/test/WindowTest.cpp \
    ../futures/test/WhenTest.cpp \
    ../futures/test/WhileDoTest.cpp

futures_test_LDADD = libfollytestmain.la
TESTS += futures_test

function_test_SOURCES = FunctionTest.cpp
function_test_LDADD = libfollytestmain.la
TESTS += function_test

check_PROGRAMS += $(TESTS)
