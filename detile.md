# 1

## command

```
./mp42ts poc1 out
```

## Asan

```bash
=================================================================
==3548425==ERROR: AddressSanitizer: heap-use-after-free on address 0x604000000090 at pc 0x5641c566ccd9 bp 0x7fffdef046e0 sp 0x7fffdef046d8
READ of size 8 at 0x604000000090 thread T0
    #0 0x5641c566ccd8 in AP4_UnknownAtom::~AP4_UnknownAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:408:25
    #1 0x5641c566bde4 in AP4_UnknownAtom::~AP4_UnknownAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:405:1
    #2 0x5641c56695ef in AP4_List<AP4_Atom>::DeleteReferences() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4List.h:476:9
    #3 0x5641c56695ef in AP4_AtomParent::~AP4_AtomParent() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:516:16
    #4 0x5641c56546d4 in AP4_File::~AP4_File() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4File.cpp:85:1
    #5 0x5641c564038e in main /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp
    #6 0x7fae84b3dd8f  (/lib/x86_64-linux-gnu/libc.so.6+0x29d8f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)
    #7 0x7fae84b3de3f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x29e3f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)
    #8 0x5641c5578a04 in _start (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0xd5a04) (BuildId: e9d01274e1656fd8)

0x604000000090 is located 0 bytes inside of 48-byte region [0x604000000090,0x6040000000c0)
freed by thread T0 here:
    #0 0x5641c5636efd in operator delete(void*) (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0x193efd) (BuildId: e9d01274e1656fd8)
    #1 0x5641c56401cc in main /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:518:9
    #2 0x7fae84b3dd8f  (/lib/x86_64-linux-gnu/libc.so.6+0x29d8f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)

previously allocated by thread T0 here:
    #0 0x5641c563669d in operator new(unsigned long) (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0x19369d) (BuildId: e9d01274e1656fd8)
    #1 0x5641c5886fde in AP4_StdcFileByteStream::Create(AP4_FileByteStream*, char const*, AP4_FileByteStream::Mode, AP4_ByteStream*&) /root/fuzzing_Bento4/Bento4/Source/C++/System/StdC/Ap4StdCFileByteStream.cpp:279:14
    #2 0x5641c5886fde in AP4_FileByteStream::Create(char const*, AP4_FileByteStream::Mode, AP4_ByteStream*&) /root/fuzzing_Bento4/Bento4/Source/C++/System/StdC/Ap4StdCFileByteStream.cpp:439:12

SUMMARY: AddressSanitizer: heap-use-after-free /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:408:25 in AP4_UnknownAtom::~AP4_UnknownAtom()
Shadow bytes around the buggy address:
  0x0c087fff7fc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff7fd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff7fe0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff7ff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff8000: fa fa fd fd fd fd fd fd fa fa 00 00 00 00 00 03
=>0x0c087fff8010: fa fa[fd]fd fd fd fd fd fa fa fa fa fa fa fa fa
  0x0c087fff8020: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c087fff8030: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c087fff8040: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c087fff8050: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c087fff8060: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
Shadow byte legend (one shadow byte represents 8 application bytes):
  Addressable:           00
  Partially addressable: 01 02 03 04 05 06 07
  Heap left redzone:       fa
  Freed heap region:       fd
  Stack left redzone:      f1
  Stack mid redzone:       f2
  Stack right redzone:     f3
  Stack after return:      f5
  Stack use after scope:   f8
  Global redzone:          f9
  Global init order:       f6
  Poisoned by user:        f7
  Container overflow:      fc
  Array cookie:            ac
  Intra object redzone:    bb
  ASan internal:           fe
  Left alloca redzone:     ca
  Right alloca redzone:    cb
==3548425==ABORTING

```

# 2

## command

```
./mp42ts poc2 out
```

## Asan

```bash
=================================================================
==4161883==ERROR: AddressSanitizer: heap-use-after-free on address 0x604000041fd8 at pc 0x55d1f5dfe011 bp 0x7ffd33aa7dc0 sp 0x7ffd33aa7db8
READ of size 8 at 0x604000041fd8 thread T0
    #0 0x55d1f5dfe010 in AP4_Sample::GetOffset() const /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Sample.h:99:48
    #1 0x55d1f5dfe010 in AP4_LinearReader::Advance(bool) /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4LinearReader.cpp:434:54
    #2 0x55d1f5dfe010 in AP4_LinearReader::ReadNextSample(unsigned int, AP4_Sample&, AP4_DataBuffer&) /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4LinearReader.cpp:530:29
    #3 0x55d1f5dfe010 in FragmentedSampleReader::ReadSample(AP4_Sample&, AP4_DataBuffer&) /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:149:29
    #4 0x55d1f5e0313e in ReadSample(SampleReader&, AP4_Track&, AP4_Sample&, AP4_DataBuffer&, double&, bool&) /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:181:32
    #5 0x55d1f5e0313e in WriteSamples(AP4_Mpeg2TsWriter&, AP4_Track*, SampleReader*, AP4_Mpeg2TsWriter::SampleStream*, AP4_Track*, SampleReader*, AP4_Mpeg2TsWriter::SampleStream*, unsigned int) /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:306:22
    #6 0x55d1f5e0313e in main /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:640:14
    #7 0x7fcf78fc9d8f  (/lib/x86_64-linux-gnu/libc.so.6+0x29d8f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)
    #8 0x7fcf78fc9e3f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x29e3f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)
    #9 0x55d1f5d38a04 in _start (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0xd5a04) (BuildId: e9d01274e1656fd8)

0x604000041fd8 is located 8 bytes inside of 48-byte region [0x604000041fd0,0x604000042000)
freed by thread T0 here:
    #0 0x55d1f5df6efd in operator delete(void*) (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0x193efd) (BuildId: e9d01274e1656fd8)
    #1 0x55d1f5dfde1b in AP4_LinearReader::SampleBuffer::~SampleBuffer() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4LinearReader.h:104:26
    #2 0x55d1f5dfde1b in AP4_LinearReader::Advance(bool) /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4LinearReader.cpp:462:17
    #3 0x55d1f5dfde1b in AP4_LinearReader::ReadNextSample(unsigned int, AP4_Sample&, AP4_DataBuffer&) /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4LinearReader.cpp:530:29
    #4 0x55d1f5dfde1b in FragmentedSampleReader::ReadSample(AP4_Sample&, AP4_DataBuffer&) /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:149:29

previously allocated by thread T0 here:
    #0 0x55d1f5df669d in operator new(unsigned long) (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0x19369d) (BuildId: e9d01274e1656fd8)
    #1 0x55d1f5dfd02e in AP4_LinearReader::Advance(bool) /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4LinearReader.cpp:422:41
    #2 0x55d1f5dfd02e in AP4_LinearReader::ReadNextSample(unsigned int, AP4_Sample&, AP4_DataBuffer&) /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4LinearReader.cpp:530:29
    #3 0x55d1f5dfd02e in FragmentedSampleReader::ReadSample(AP4_Sample&, AP4_DataBuffer&) /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:149:29

SUMMARY: AddressSanitizer: heap-use-after-free /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Sample.h:99:48 in AP4_Sample::GetOffset() const
Shadow bytes around the buggy address:
  0x0c08800003a0: fa fa fd fd fd fd fd fa fa fa fd fd fd fd fd fd
  0x0c08800003b0: fa fa fd fd fd fd fd fa fa fa fd fd fd fd fd fd
  0x0c08800003c0: fa fa fd fd fd fd fd fa fa fa fd fd fd fd fd fd
  0x0c08800003d0: fa fa fd fd fd fd fd fa fa fa fd fd fd fd fd fd
  0x0c08800003e0: fa fa fd fd fd fd fd fa fa fa fd fd fd fd fd fd
=>0x0c08800003f0: fa fa fd fd fd fd fd fa fa fa fd[fd]fd fd fd fd
  0x0c0880000400: fa fa fd fd fd fd fd fa fa fa fa fa fa fa fa fa
  0x0c0880000410: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c0880000420: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c0880000430: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
  0x0c0880000440: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
Shadow byte legend (one shadow byte represents 8 application bytes):
  Addressable:           00
  Partially addressable: 01 02 03 04 05 06 07
  Heap left redzone:       fa
  Freed heap region:       fd
  Stack left redzone:      f1
  Stack mid redzone:       f2
  Stack right redzone:     f3
  Stack after return:      f5
  Stack use after scope:   f8
  Global redzone:          f9
  Global init order:       f6
  Poisoned by user:        f7
  Container overflow:      fc
  Array cookie:            ac
  Intra object redzone:    bb
  ASan internal:           fe
  Left alloca redzone:     ca
  Right alloca redzone:    cb
==4161883==ABORTING

```

# 3

## command

```
./mp42ts poc3 out
```

```bash
=================================================================
==745950==ERROR: AddressSanitizer: heap-use-after-free on address 0x604000000090 at pc 0x55b502e866f0 bp 0x7ffc9dbf2600 sp 0x7ffc9dbf25f8
READ of size 8 at 0x604000000090 thread T0
    #0 0x55b502e866ef in AP4_SubStream::~AP4_SubStream() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ByteStream.cpp:428:17
    #1 0x55b502e85924 in AP4_SubStream::~AP4_SubStream() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ByteStream.cpp:427:1
    #2 0x55b5030babf4 in AP4_DataAtom::~AP4_DataAtom() /root/fuzzing_Bento4/Bento4/Source/C++/MetaData/Ap4MetaData.cpp:1453:1
    #3 0x55b502ea35ef in AP4_List<AP4_Atom>::DeleteReferences() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4List.h:476:9
    #4 0x55b502ea35ef in AP4_AtomParent::~AP4_AtomParent() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:516:16
    #5 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #6 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #7 0x55b502ea35ef in AP4_List<AP4_Atom>::DeleteReferences() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4List.h:476:9
    #8 0x55b502ea35ef in AP4_AtomParent::~AP4_AtomParent() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:516:16
    #9 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #10 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #11 0x55b502ea35ef in AP4_List<AP4_Atom>::DeleteReferences() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4List.h:476:9
    #12 0x55b502ea35ef in AP4_AtomParent::~AP4_AtomParent() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:516:16
    #13 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #14 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #15 0x55b502ea35ef in AP4_List<AP4_Atom>::DeleteReferences() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4List.h:476:9
    #16 0x55b502ea35ef in AP4_AtomParent::~AP4_AtomParent() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:516:16
    #17 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #18 0x55b502ed4048 in AP4_ContainerAtom::~AP4_ContainerAtom() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ContainerAtom.h:48:7
    #19 0x55b502ea35ef in AP4_List<AP4_Atom>::DeleteReferences() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4List.h:476:9
    #20 0x55b502ea35ef in AP4_AtomParent::~AP4_AtomParent() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4Atom.cpp:516:16
    #21 0x55b502e8e6d4 in AP4_File::~AP4_File() /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4File.cpp:85:1
    #22 0x55b502e7a38e in main /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp
    #23 0x7faf821abd8f  (/lib/x86_64-linux-gnu/libc.so.6+0x29d8f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)
    #24 0x7faf821abe3f in __libc_start_main (/lib/x86_64-linux-gnu/libc.so.6+0x29e3f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)
    #25 0x55b502db2a04 in _start (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0xd5a04) (BuildId: e9d01274e1656fd8)

0x604000000090 is located 0 bytes inside of 48-byte region [0x604000000090,0x6040000000c0)
freed by thread T0 here:
    #0 0x55b502e70efd in operator delete(void*) (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0x193efd) (BuildId: e9d01274e1656fd8)
    #1 0x55b502e7a1cc in main /root/fuzzing_Bento4/Bento4/Source/C++/Apps/Mp42Ts/Mp42Ts.cpp:518:9
    #2 0x7faf821abd8f  (/lib/x86_64-linux-gnu/libc.so.6+0x29d8f) (BuildId: c289da5071a3399de893d2af81d6a30c62646e1e)

previously allocated by thread T0 here:
    #0 0x55b502e7069d in operator new(unsigned long) (/root/fuzzing_Bento4/Bento4/cmakebuild/mp42ts+0x19369d) (BuildId: e9d01274e1656fd8)
    #1 0x55b5030c0fde in AP4_StdcFileByteStream::Create(AP4_FileByteStream*, char const*, AP4_FileByteStream::Mode, AP4_ByteStream*&) /root/fuzzing_Bento4/Bento4/Source/C++/System/StdC/Ap4StdCFileByteStream.cpp:279:14
    #2 0x55b5030c0fde in AP4_FileByteStream::Create(char const*, AP4_FileByteStream::Mode, AP4_ByteStream*&) /root/fuzzing_Bento4/Bento4/Source/C++/System/StdC/Ap4StdCFileByteStream.cpp:439:12

SUMMARY: AddressSanitizer: heap-use-after-free /root/fuzzing_Bento4/Bento4/Source/C++/Core/Ap4ByteStream.cpp:428:17 in AP4_SubStream::~AP4_SubStream()
Shadow bytes around the buggy address:
  0x0c087fff7fc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff7fd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff7fe0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff7ff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c087fff8000: fa fa fd fd fd fd fd fd fa fa 00 00 00 00 00 03
=>0x0c087fff8010: fa fa[fd]fd fd fd fd fd fa fa fd fd fd fd fd fd
  0x0c087fff8020: fa fa fd fd fd fd fd fd fa fa fd fd fd fd fd fd
  0x0c087fff8030: fa fa fd fd fd fd fd fd fa fa fd fd fd fd fd fd
  0x0c087fff8040: fa fa fd fd fd fd fd fd fa fa fd fd fd fd fd fd
  0x0c087fff8050: fa fa fd fd fd fd fd fd fa fa fd fd fd fd fd fd
  0x0c087fff8060: fa fa fd fd fd fd fd fd fa fa fd fd fd fd fd fd
Shadow byte legend (one shadow byte represents 8 application bytes):
  Addressable:           00
  Partially addressable: 01 02 03 04 05 06 07
  Heap left redzone:       fa
  Freed heap region:       fd
  Stack left redzone:      f1
  Stack mid redzone:       f2
  Stack right redzone:     f3
  Stack after return:      f5
  Stack use after scope:   f8
  Global redzone:          f9
  Global init order:       f6
  Poisoned by user:        f7
  Container overflow:      fc
  Array cookie:            ac
  Intra object redzone:    bb
  ASan internal:           fe
  Left alloca redzone:     ca
  Right alloca redzone:    cb
==745950==ABORTING

```

