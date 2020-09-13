---
title: ARM64 內建
description: Visual Studio 中 Microsoft c + + 編譯器所支援的 ARM64 內建函式的參考清單。
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
helpviewer_keywords:
- __break ARM64 intrinsic
- __addx18byte ARM64 intrinsic
- __addx18word ARM64 intrinsic
- __addx18dword ARM64 intrinsic
- __addx18qword ARM64 intrinsic
- __cas8 ARM64 intrinsic
- __cas16 ARM64 intrinsic
- __cas32 ARM64 intrinsic
- __cas64 ARM64 intrinsic
- __casa8 ARM64 intrinsic
- __casa16 ARM64 intrinsic
- __casa32 ARM64 intrinsic
- __casa64 ARM64 intrinsic
- __casl8 ARM64 intrinsic
- __casl16 ARM64 intrinsic
- __casl32 ARM64 intrinsic
- __casl64 ARM64 intrinsic
- __casal8 ARM64 intrinsic
- __casal16 ARM64 intrinsic
- __casal32 ARM64 intrinsic
- __casal64 ARM64 intrinsic
- __crc32b ARM64 intrinsic
- __crc32h ARM64 intrinsic
- __crc32w ARM64 intrinsic
- __crc32d ARM64 intrinsic
- __crc32cb ARM64 intrinsic
- __crc32ch ARM64 intrinsic
- __crc32cw ARM64 intrinsic
- __crc32cd ARM64 intrinsic
- __getReg ARM64 intrinsic
- __getRegFp ARM64 intrinsic
- __getCallerReg ARM64 intrinsic
- __getCallerRegFp ARM64 intrinsic
- __hlt ARM64 intrinsic
- __incx18byte ARM64 intrinsic
- __incx18word ARM64 intrinsic
- __incx18dword ARM64 intrinsic
- __incx18qword ARM64 intrinsic
- __ldar8 ARM64 intrinsic
- __ldar16 ARM64 intrinsic
- __ldar32 ARM64 intrinsic
- __ldar64 ARM64 intrinsic
- __ldapr8 ARM64 intrinsic
- __ldapr16 ARM64 intrinsic
- __ldapr32 ARM64 intrinsic
- __ldapr64 ARM64 intrinsic
- __prefetch2 ARM64 intrinsic
- __readx18byte ARM64 intrinsic
- __readx18word ARM64 intrinsic
- __readx18dword ARM64 intrinsic
- __readx18qword ARM64 intrinsic
- __setReg ARM64 intrinsic
- __setRegFp ARM64 intrinsic
- __setCallerReg ARM64 intrinsic
- __setCallerRegFp ARM64 intrinsic
- __stlr8 ARM64 intrinsic
- __stlr16 ARM64 intrinsic
- __stlr32 ARM64 intrinsic
- __stlr64 ARM64 intrinsic
- __swp8 ARM64 intrinsic
- __swp16 ARM64 intrinsic
- __swp32 ARM64 intrinsic
- __swp64 ARM64 intrinsic
- __swpa8 ARM64 intrinsic
- __swpa16 ARM64 intrinsic
- __swpa32 ARM64 intrinsic
- __swpa64 ARM64 intrinsic
- __swpl8 ARM64 intrinsic
- __swpl16 ARM64 intrinsic
- __swpl32 ARM64 intrinsic
- __swpl64 ARM64 intrinsic
- __swpal8 ARM64 intrinsic
- __swpal16 ARM64 intrinsic
- __swpal32 ARM64 intrinsic
- __swpal64 ARM64 intrinsic
- __sys ARM64 intrinsic
- __svc ARM64 intrinsic
- __writex18byte ARM64 intrinsic
- __writex18word ARM64 intrinsic
- __writex18dword ARM64 intrinsic
- __writex18qword ARM64 intrinsic
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 13358458bf9abcf0bc6e38ca115b537abc99300a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039751"
---
# <a name="arm64-intrinsics"></a>ARM64 內建

Microsoft c + + 編譯器 (MSVC) 會在 ARM64 架構上提供下列內建函式。 如需 ARM 的詳細資訊，請參閱 [Arm 開發人員檔](https://developer.arm.com/docs) 網站的架構和軟體發展工具章節。

## <a name="neon"></a><a name="top"></a> 霓虹燈

適用于 ARM64 的霓虹燈向量指令集延伸模組提供單指令多資料 (SIMD) 功能。 它們類似于 x86 和 x64 架構處理器通用的 MMX 和 SSE 向量指令集中的專案。

在標頭檔 *arm64_neon*中提供支援的霓虹燈內建函式。 霓虹燈內建的 MSVC 支援類似于 ARM64 編譯器，其記載于 ARM 資訊中心網站上的 [ARM 霓虹燈內部參考](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) 。

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a> ARM64 特定的內建函式清單

|函數名稱|指令|函式原型|
|-------------------|-----------------|------------------------|
|__break|BRK|void __break (int) |
|__addx18byte||void __addx18byte (不帶正負號的 long、不帶正負號的 char) |
|__addx18word||void __addx18word (不帶正負號的 long、不帶正負號的 short) |
|__addx18dword||void __addx18dword (不帶正負號的 long、不帶正負號的 long) |
|__addx18qword||void __addx18qword (不帶正負號的 long、不帶正負號的 __int64) |
|__cas8|CASB|未簽署的 __int8 __cas8 (不帶正負號 __int8 volatile * _Target、未簽署的 __int8 _Comp、未簽署的 __int8 _Value) |
|__cas16|現金|未簽署的 __int16 __cas16 (不帶正負號 __int16 volatile * _Target、未簽署的 __int16 _Comp、未簽署的 __int16 _Value) |
|__cas32|CAS|未簽署的 __int32 __cas32 (不帶正負號 __int32 volatile * _Target、未簽署的 __int32 _Comp、未簽署的 __int32 _Value) |
|__cas64|CAS|未簽署的 __int64 __cas64 (不帶正負號 __int64 volatile * _Target、未簽署的 __int64 _Comp、未簽署的 __int64 _Value) |
|__casa8|CASAB|未簽署的 __int8 __casa8 (不帶正負號 __int8 volatile * _Target、未簽署的 __int8 _Comp、未簽署的 __int8 _Value) |
|__casa16|CASAH|未簽署的 __int16 __casa16 (不帶正負號 __int16 volatile * _Target、未簽署的 __int16 _Comp、未簽署的 __int16 _Value) |
|__casa32|CASA|未簽署的 __int32 __casa32 (不帶正負號 __int32 volatile * _Target、未簽署的 __int32 _Comp、未簽署的 __int32 _Value) |
|__casa64|CASA|未簽署的 __int64 __casa64 (不帶正負號 __int64 volatile * _Target、未簽署的 __int64 _Comp、未簽署的 __int64 _Value) |
|__casl8|CASLB|未簽署的 __int8 __casl8 (不帶正負號 __int8 volatile * _Target、未簽署的 __int8 _Comp、未簽署的 __int8 _Value) |
|__casl16|CASLH|未簽署的 __int16 __casl16 (不帶正負號 __int16 volatile * _Target、未簽署的 __int16 _Comp、未簽署的 __int16 _Value) |
|__casl32|CASL|未簽署的 __int32 __casl32 (不帶正負號 __int32 volatile * _Target、未簽署的 __int32 _Comp、未簽署的 __int32 _Value) |
|__casl64|CASL|未簽署的 __int64 __casl64 (不帶正負號 __int64 volatile * _Target、未簽署的 __int64 _Comp、未簽署的 __int64 _Value) |
|__casal8|CASALB|未簽署的 __int8 __casal8 (不帶正負號 __int8 volatile * _Target、未簽署的 __int8 _Comp、未簽署的 __int8 _Value) |
|__casal16|CASALH|未簽署的 __int16 __casal16 (不帶正負號 __int16 volatile * _Target、未簽署的 __int16 _Comp、未簽署的 __int16 _Value) |
|__casal32|CASAL|未簽署的 __int32 __casal32 (不帶正負號 __int32 volatile * _Target、未簽署的 __int32 _Comp、未簽署的 __int32 _Value) |
|__casal64|CASAL|未簽署的 __int64 __casal64 (不帶正負號 __int64 volatile * _Target、未簽署的 __int64 _Comp、未簽署的 __int64 _Value) |
|__crc32b|CRC32B|未簽署的 __int32 __crc32b (未簽署的 __int32、未簽署的 __int32) |
|__crc32h|CRC32H|未簽署的 __int32 __crc32h (未簽署的 __int32、未簽署的 __int32) |
|__crc32w|CRC32W|未簽署的 __int32 __crc32w (未簽署的 __int32、未簽署的 __int32) |
|__crc32d|CRC32X|未簽署的 __int32 __crc32d (未簽署的 __int32、未簽署的 __int64) |
|__crc32cb|CRC32CB|未簽署的 __int32 __crc32cb (未簽署的 __int32、未簽署的 __int32) |
|__crc32ch|CRC32CH|未簽署的 __int32 __crc32ch (未簽署的 __int32、未簽署的 __int32) |
|__crc32cw|CRC32CW|未簽署的 __int32 __crc32cw (未簽署的 __int32、未簽署的 __int32) |
|__crc32cd|CRC32CX|未簽署的 __int32 __crc32cd (未簽署的 __int32、未簽署的 __int64) |
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> 將記憶體屏障作業插入指令資料流中。 參數 `_Type` 會指定屏障強制執行的限制類型。<br /><br /> 如需可強制執行的限制類型的詳細資訊，請參閱 [記憶體屏障限制](#BarrierRestrictions)。|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> 將記憶體屏障作業插入指令資料流中。 參數 `_Type` 會指定屏障強制執行的限制類型。<br /><br /> 如需可強制執行的限制類型的詳細資訊，請參閱 [記憶體屏障限制](#BarrierRestrictions)。|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> 將記憶體屏障作業插入指令資料流中。 參數 `_Type` 會指定屏障強制執行的限制類型。<br /><br /> 如需可強制執行的限制類型的詳細資訊，請參閱 [記憶體屏障限制](#BarrierRestrictions)。|
|__getReg||不帶正負號的 __int64 __getReg (int) |
|__getRegFp||double __getRegFp (int) |
|__getCallerReg||不帶正負號的 __int64 __getCallerReg (int) |
|__getCallerRegFp||double __getCallerRegFp (int) |
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt (不帶正負號的 int，... ) |
|__incx18byte||void __incx18byte (不帶正負號的 long) |
|__incx18word||void __incx18word (不帶正負號的 long) |
|__incx18dword||void __incx18dword (不帶正負號的 long) |
|__incx18qword||void __incx18qword (不帶正負號的 long) |
|__iso_volatile_load16||__int16 \_ _iso_volatile_load16 (const volatile \_ _int16 \*) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__iso_volatile_load32||__int32 \_ _iso_volatile_load32 (const volatile \_ _int32 \*) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__iso_volatile_load64||__int64 \_ _iso_volatile_load64 (const volatile \_ _int64 \*) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__iso_volatile_load8||__int8 \_ _iso_volatile_load8 (const volatile \_ _int8 \*) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__iso_volatile_store16||void __iso_volatile_store16 (volatile \_ _int16 \* ， \_ _int16) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__iso_volatile_store32||void __iso_volatile_store32 (volatile \_ _int32 \* ， \_ _int32) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__iso_volatile_store64||void __iso_volatile_store64 (volatile \_ _int64 \* ， \_ _int64) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__iso_volatile_store8||void __iso_volatile_store8 (volatile \_ _int8 \* ， \_ _int8) <br /><br /> 如需詳細資訊，請參閱 [__iso_volatile_load/store 內建函式](#IsoVolatileLoadStore)。|
|__ldar8|LDARB|未簽署的 __int8 __ldar8 (不帶正負號的 __int8 volatile * _Target) |
|__ldar16|LDARH|未簽署的 __int16 __ldar16 (不帶正負號的 __int16 volatile * _Target) |
|__ldar32|LDAR|未簽署的 __int32 __ldar32 (不帶正負號的 __int32 volatile * _Target) |
|__ldar64|LDAR|未簽署的 __int64 __ldar64 (不帶正負號的 __int64 volatile * _Target) |
|__ldapr8|LDAPRB|未簽署的 __int8 __ldapr8 (不帶正負號的 __int8 volatile * _Target) |
|__ldapr16|LDAPRH|未簽署的 __int16 __ldapr16 (不帶正負號的 __int16 volatile * _Target) |
|__ldapr32|LDAPR|未簽署的 __int32 __ldapr32 (不帶正負號的 __int32 volatile * _Target) |
|__ldapr64|LDAPR|未簽署的 __int64 __ldapr64 (不帶正負號的 __int64 volatile * _Target) |
|__mulh||\__int64 __mulh (\_ _int64， \_ _int64) |
|__prefetch|PRFM|void __cdecl \_ _prefetch (const void \*) <br /><br /> 提供 `PRFM` 記憶體提示，其中包含系統的預先提取作業 `PLDL1KEEP` ，可能很快就會存取指定位址附近的記憶體。 有些系統可能會選擇最佳化此記憶體存取模式，來增加執行階段效能。 不過，從 C++ 語言的觀點來看，函式沒有顯著的影響，而且可能根本不執行任何動作。|
|__prefetch2|PRFM|void __cdecl \_ _prefetch (const void \* ，uint8_t prfop) <br /><br /> 提供 `PRFM` 記憶體提示，其中包含提供的預先提取作業，可讓系統在指定位址附近或附近存取記憶體。 有些系統可能會選擇最佳化此記憶體存取模式，來增加執行階段效能。 不過，從 C++ 語言的觀點來看，函式沒有顯著的影響，而且可能根本不執行任何動作。|
|__readx18byte||未簽署的 char __readx18byte (不帶正負號的 long) |
|__readx18word||未簽署的短 __readx18word (不帶正負號的 long) |
|__readx18dword||未簽署的 long __readx18dword (不帶正負號的 long) |
|__readx18qword||未簽署的 __int64 __readx18qword (不帶正負號的 long) |
|__setReg||void __setReg (int、未簽署的 __int64) |
|__setRegFp||void __setRegFp (int，double) |
|__setCallerReg||void __setCallerReg (int、未簽署的 __int64) |
|__setCallerRegFp||void __setCallerRegFp (int，double) |
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert (int，const char \*) |
|__stlr8|STLRB|void __stlr8 (未簽署 __int8 volatile * _Target、未簽署的 __int8 _Value) |
|__stlr16|STLRH|void __stlr16 (未簽署 __int16 volatile * _Target、未簽署的 __int16 _Value) |
|__stlr32|STLR|void __stlr32 (未簽署 __int32 volatile * _Target、未簽署的 __int32 _Value) |
|__stlr64|STLR|void __stlr64 (未簽署 __int64 volatile * _Target、未簽署的 __int64 _Value) |
|__swp8|SWPB|未簽署的 __int8 __swp8 (不帶正負號的 __int8 volatile * _Target、未簽署的 __int8 _Value) |
|__swp16|SWPH|未簽署的 __int16 __swp16 (不帶正負號的 __int16 volatile * _Target、未簽署的 __int16 _Value) |
|__swp32|SWP|未簽署的 __int32 __swp32 (不帶正負號的 __int32 volatile * _Target、未簽署的 __int32 _Value) |
|__swp64|SWP|未簽署的 __int64 __swp64 (不帶正負號的 __int64 volatile * _Target、未簽署的 __int64 _Value) |
|__swpa8|SWPAB|未簽署的 __int8 __swpa8 (不帶正負號的 __int8 volatile * _Target、未簽署的 __int8 _Value) |
|__swpa16|SWPAH|未簽署的 __int16 __swpa16 (不帶正負號的 __int16 volatile * _Target、未簽署的 __int16 _Value) |
|__swpa32|SWPA|未簽署的 __int32 __swpa32 (不帶正負號的 __int32 volatile * _Target、未簽署的 __int32 _Value) |
|__swpa64|SWPA|未簽署的 __int64 __swpa64 (不帶正負號的 __int64 volatile * _Target、未簽署的 __int64 _Value) |
|__swpl8|SWPLB|未簽署的 __int8 __swpl8 (不帶正負號的 __int8 volatile * _Target、未簽署的 __int8 _Value) |
|__swpl16|SWPLH|未簽署的 __int16 __swpl16 (不帶正負號的 __int16 volatile * _Target、未簽署的 __int16 _Value) |
|__swpl32|SWPL|未簽署的 __int32 __swpl32 (不帶正負號的 __int32 volatile * _Target、未簽署的 __int32 _Value) |
|__swpl64|SWPL|未簽署的 __int64 __swpl64 (不帶正負號的 __int64 volatile * _Target、未簽署的 __int64 _Value) |
|__swpal8|SWPALB|未簽署的 __int8 __swpal8 (不帶正負號的 __int8 volatile * _Target、未簽署的 __int8 _Value) |
|__swpal16|SWPALH|未簽署的 __int16 __swpal16 (不帶正負號的 __int16 volatile * _Target、未簽署的 __int16 _Value) |
|__swpal32|SWPAL|未簽署的 __int32 __swpal32 (不帶正負號的 __int32 volatile * _Target、未簽署的 __int32 _Value) |
|__swpal64|SWPAL|未簽署的 __int64 __swpal64 (不帶正負號的 __int64 volatile * _Target、未簽署的 __int64 _Value) |
|__sys|SYS|不帶正負號的 int __sys (int，__int64) |
|__svc|SVC|不帶正負號的 int __svc (不帶正負號的 int，... ) |
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||void __writex18byte (不帶正負號的 long、不帶正負號的 char) |
|__writex18word||void __writex18word (不帶正負號的 long、不帶正負號的 short) |
|__writex18dword||void __writex18dword (不帶正負號的 long、不帶正負號的 long) |
|__writex18qword||void __writex18qword (不帶正負號的 long、不帶正負號的 __int64) |
|__umulh||未簽署 \_ 的 _int64 __umulh (未簽署 \_ 的 _int64、未簽署的 \_ _int64) |
|_CopyDoubleFromInt64||雙 _CopyDoubleFromInt64 (\_ _int64) |
|_CopyFloatFromInt32||float _CopyFloatFromInt32 (\_ _int32) |
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||不帶正負號的 int _CountLeadingOnes64 (未簽署的 \_ _int64) |
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||不帶正負號的 int _CountLeadingSigns64 (\_ _int64) |
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||不帶正負號的 int _CountLeadingZeros64 (未簽署的 \_ _int64) |
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg (int) |
|_WriteStatusReg|MSR|void _WriteStatusReg (int， \_ _int64) |

[[回到頁首](#top)]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a> 記憶體屏障限制

內建函式 `__dmb` (資料記憶體屏障) 、 `__dsb` (資料同步處理屏障) ，以及 `__isb` (指令同步處理屏障) 使用下列預先定義的值，根據共用網域以及受作業影響的存取類型來指定記憶體屏障限制。

|限制值|描述|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|完整系統，讀取和寫入。|
|_ARM64_BARRIER_ST|完整系統，只寫入。|
|_ARM64_BARRIER_LD|完整系統、唯讀。|
|_ARM64_BARRIER_ISH|可內部共用，讀取和寫入。|
|_ARM64_BARRIER_ISHST|可內部共用，只寫入。|
|_ARM64_BARRIER_ISHLD|內部可共用的唯讀。|
|_ARM64_BARRIER_NSH|不可共用，讀取和寫入。|
|_ARM64_BARRIER_NSHST|不可共用，只寫入。|
|_ARM64_BARRIER_NSHLD|不可共用的唯讀。|
|_ARM64_BARRIER_OSH|可外部共用，讀取和寫入。|
|_ARM64_BARRIER_OSHST|可外部共用，只寫入。|
|_ARM64_BARRIER_OSHLD|外部可共用的唯讀。|

對於內建 `__isb` 而言，目前唯一有效的限制是 _ARM64_BARRIER_SY; 所有其他值都是由架構保留。

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a> __iso_volatile_load/store 內建函式

這些內建函式會明確地執行不受編譯器優化的載入和存放區。

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>參數

*位置*\
要讀取或寫入的記憶體位置的位址。

*Value*\
要寫入指定記憶體位置的值 (儲存僅限) 的內建函式。

#### <a name="return-value-load-intrinsics-only"></a>傳回值 (僅載入內建函式) 

*位置*所指定之記憶體位置的值。

#### <a name="remarks"></a>備註

您可以使用 `__iso_volatile_load8/16/32/64` 和 `__iso_volatile_store8/16/32/64` 內建函式明確地執行不受編譯器優化的記憶體存取。 編譯器無法移除、synthetize 或變更這些作業的相對順序。 但是，它不會產生隱含硬體記憶體阻礙。 因此，硬體可能仍然重新排列跨多個執行緒中可觀察到的記憶體存取。 更精確地說，這些內建函式相當於在 **/volatile： iso**下編譯的下列運算式。

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

請注意，內建函式採取暫時性 (volatile) 指標以容納暫時性變數。 不過，使用 volatile 指標做為引數並沒有任何需求或建議。 如果使用一般的非暫時性型別，則這些作業的語法會完全相同。

如需有關 **/volatile： iso** 命令列引數的詳細資訊，請參閱 [/volatile (volatile 關鍵字轉譯) ](../build/reference/volatile-volatile-keyword-interpretation.md)。

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a> 從其他架構 ARM64 的內建函式支援

下表列出 ARM64 平臺上支援的其他架構內建函式。 在 ARM64 上內建的行為與其他硬體架構上的行為有何不同，將會注明其他詳細資料。

|函數名稱|函式原型|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg (const char \*) |
|__debugbreak|void __cdecl \_ _debugbreak (void) |
|__fastfail|__declspec (noreturn) void \_ _fastfail (不帶正負號的 int) |
|__nop|void __nop(void)|
|__yield|void __yield (void) **注意：**  在 ARM64 平臺上，此函數會產生 yield 指令。 此指令表示執行緒正在執行可能暫時暫停執行的工作（例如，spinlock），而不會對程式造成不良影響。 它可讓 CPU 在執行迴圈期間執行其他工作，否則將會浪費。|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void) |
|_BitScanForward|不帶正負號的 char _BitScanForward (不帶正負號 \* 的 long _Index、不) _Mask 帶正負號|
|_BitScanForward64|不帶正負號的 char _BitScanForward64 (不帶正負號 \* 的 long _Index、未簽署的 _Mask __int64|
|_BitScanReverse|不帶正負號的 char _BitScanReverse (不帶正負號 \* 的 long _Index、不) _Mask 帶正負號|
|_BitScanReverse64|不帶正負號的 char _BitScanReverse64 (不帶正負號 \* 的 long _Index、未簽署的 _Mask __int64|
|_bittest|不帶正負號的 char _bittest (long const \* 、long) |
|_bittest64|不帶正負號的 char _bittest64 (__int64 const \* ，__int64) |
|_bittestandcomplement|不帶正負號的 char _bittestandcomplement (long \* ，long) |
|_bittestandcomplement64|不帶正負號的 char _bittestandcomplement64 (__int64 \* ，__int64) |
|_bittestandreset|不帶正負號的 char _bittestandreset (long \* ，long) |
|_bittestandreset64|不帶正負號的 char _bittestandreset64 (__int64 \* ，__int64) |
|_bittestandset|不帶正負號的 char _bittestandset (long \* ，long) |
|_bittestandset64|不帶正負號的 char _bittestandset64 (__int64 \* ，__int64) |
|_byteswap_uint64|未簽署的 __int64 \_ _cdecl _byteswap_uint64 (不帶正負號的 \_ _int64) |
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable (void) **注意：**  在 ARM64 平臺上，此函式會產生指示， `MSR DAIFCLR,#2` 僅供內建函式使用。|
|_enable|void __cdecl _enable (void) **注意：**  在 ARM64 平臺上，此函式會產生指示， `MSR DAIFSET,#2` 僅供內建函式使用。|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress (void) |
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|未簽署 \_ 的 __int64 _cdecl _rotl64 (不帶正負號 \_ 的 _int64 _Value、int _Shift) |
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|未簽署 \_ 的 __int64 _cdecl _rotr64 (不帶正負號 \_ 的 _int64 _Value、int _Shift) |
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[回到頁首](#top)]

## <a name="interlocked-intrinsics"></a>連鎖內建函式

連鎖內建函式是一組內建函式，用來執行不可部分完成的讀取-修改-寫入作業。 其中有部分通用於所有平台。 因為有大量的專案，所以它們會分別列在這裡。 因為它們的定義大多是多餘的，所以在一般的情況下，比較容易考慮它們。 它們的名稱可以用來得出確切的行為。

下表摘要說明非 bittest 連鎖內建函式的 ARM64 支援。 在表中的每個儲存格對應的名稱，是將列的最左邊儲存格的作業名稱，和欄的最上方儲存格的類型名稱，附加至 `_Interlocked` 所衍生的名稱。 例如，資料列和資料行交集處的資料格 `Xor` `8` 會對應至 `_InterlockedXor8` ，而且完全受到支援。 大部分受支援的函式會提供這些選擇性的字尾：`_acq`、`_rel` 和 `_nf`。 `_acq` 字尾表示「取得」語意，`_rel` 字尾表示「釋放」語意。 或「無範圍」 `_nf` 尾碼對 ARM 和 ARM64 而言是唯一的，並在下一節中討論。

|作業|8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|加|None|None|完整|完整|None|None|
|And|完整|完整|完整|完整|None|None|
|CompareExchange|完整|完整|完整|完整|完整|完整|
|遞減|None|完整|完整|完整|None|None|
|Exchange|完整|完整|完整|完整|None|完整|
|ExchangeAdd|完整|完整|完整|完整|None|None|
|[遞增]|None|完整|完整|完整|None|None|
|或|完整|完整|完整|完整|None|None|
|Xor|完整|完整|完整|完整|None|None|

索引鍵：

- **Full**：支援純、 `_acq` 、 `_rel` 和 `_nf` 表單。

- **無**：不支援

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a> _nf (沒有任何隔離) 尾碼

或「無範圍」 `_nf` 尾碼表示作業的行為不像任何類型的記憶體屏障，相較于其他三種形式的 (單純的、 `_acq` 和 `_rel`) ，它們全都會以某種類型的關卡來運作。 表單的其中一個可能用途 `_nf` 是維護一個統計資料計數器，此計數器會由多個執行緒同時更新，但在執行多個執行緒時，不會使用其值。

### <a name="list-of-interlocked-intrinsics"></a>連鎖內建函式的清單

|函數名稱|函式原型|
|-------------------|------------------------|
|_InterlockedAdd|long _InterlockedAdd (long _volatile \* 、long) |
|_InterlockedAdd64|__int64 _InterlockedAdd64 (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAdd_acq|long _InterlockedAdd_acq (long volatile \* 、long) |
|_InterlockedAdd_nf|long _InterlockedAdd_nf (long volatile \* 、long) |
|_InterlockedAdd_rel|long _InterlockedAdd_rel (long volatile \* 、long) |
|_InterlockedAnd|long _InterlockedAnd (long volatile \* 、long) |
|_InterlockedAnd16|簡短的 _InterlockedAnd16 (short volatile \* 、short) |
|_InterlockedAnd16_acq|簡短的 _InterlockedAnd16_acq (short volatile \* 、short) |
|_InterlockedAnd16_nf|簡短的 _InterlockedAnd16_nf (short volatile \* 、short) |
|_InterlockedAnd16_rel|簡短的 _InterlockedAnd16_rel (short volatile \* 、short) |
|_InterlockedAnd64|__int64 _InterlockedAnd64 (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedAnd8|char _InterlockedAnd8 (char volatile \* ，char) |
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq (char volatile \* ，char) |
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (char volatile \* ，char) |
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel (char volatile \* ，char) |
|_InterlockedAnd_acq|long _InterlockedAnd_acq (long volatile \* 、long) |
|_InterlockedAnd_nf|long _InterlockedAnd_nf (long volatile \* 、long) |
|_InterlockedAnd_rel|long _InterlockedAnd_rel (long volatile \* 、long) |
|_InterlockedCompareExchange|long __cdecl _InterlockedCompareExchange (long volatile \* 、long、long) |
|_InterlockedCompareExchange_acq|long _InterlockedCompareExchange_acq (long volatile \* 、long、long) |
|_InterlockedCompareExchange_nf|long _InterlockedCompareExchange_nf (long volatile \* 、long、long) |
|_InterlockedCompareExchange_rel|long _InterlockedCompareExchange_rel (long volatile \* 、long、long) |
|_InterlockedCompareExchange16|short _InterlockedCompareExchange16 (short volatile \* 、short、short) |
|_InterlockedCompareExchange16_acq|short _InterlockedCompareExchange16_acq (short volatile \* 、short、short) |
|_InterlockedCompareExchange16_nf|short _InterlockedCompareExchange16_nf (short volatile \* 、short、short) |
|_InterlockedCompareExchange16_rel|short _InterlockedCompareExchange16_rel (short volatile \* 、short、short) |
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 (\_ _int64 volatile \* 、 \_ _int64、_int64 \_) |
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq (\_ _int64 volatile \* 、 \_ _int64、_int64 \_) |
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf (\_ _int64 volatile \* 、 \_ _int64、_int64 \_) |
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel (\_ _int64 volatile \* 、 \_ _int64、_int64 \_) |
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char volatile \* 、char、char) |
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char volatile \* 、char、char) |
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (char volatile \* 、char、char) |
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (char volatile \* 、char、char) |
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \* 、void \* 、void \*) |
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* volatile \* 、void \* 、void \*) |
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \* 、void \* 、void \*) |
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \* 、void \* 、void \*) |
|_InterlockedCompareExchange128|不帶正負號的 char _InterlockedCompareExchange128 (\_ _int64 volatile \* _Destination，_int64 _ExchangeHigh，_int64 _ExchangeLow \_ \_ ， \_ _int64 \* _ComparandResult) |
|_InterlockedCompareExchange128_acq|不帶正負號的 char _InterlockedCompareExchange128_acq (\_ _int64 volatile \* _Destination，_int64 _ExchangeHigh，_int64 _ExchangeLow \_ \_ ， \_ _int64 \* _ComparandResult) |
|_InterlockedCompareExchange128_nf|不帶正負號的 char _InterlockedCompareExchange128_nf (\_ _int64 volatile \* _Destination，_int64 _ExchangeHigh，_int64 _ExchangeLow \_ \_ ， \_ _int64 \* _ComparandResult) |
|_InterlockedCompareExchange128_rel|不帶正負號的 char _InterlockedCompareExchange128_rel (\_ _int64 volatile \* _Destination，_int64 _ExchangeHigh，_int64 _ExchangeLow \_ \_ ， \_ _int64 \* _ComparandResult) |
|_InterlockedDecrement|long __cdecl _InterlockedDecrement (long volatile \*) |
|_InterlockedDecrement16|簡短 _InterlockedDecrement16 (短 volatile \*) |
|_InterlockedDecrement16_acq|簡短 _InterlockedDecrement16_acq (短 volatile \*) |
|_InterlockedDecrement16_nf|簡短 _InterlockedDecrement16_nf (短 volatile \*) |
|_InterlockedDecrement16_rel|簡短 _InterlockedDecrement16_rel (短 volatile \*) |
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\_ _int64 volatile \*) |
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq (\_ _int64 volatile \*) |
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf (\_ _int64 volatile \*) |
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\_ _int64 volatile \*) |
|_InterlockedDecrement_acq|long _InterlockedDecrement_acq (long volatile \*) |
|_InterlockedDecrement_nf|long _InterlockedDecrement_nf (long volatile \*) |
|_InterlockedDecrement_rel|long _InterlockedDecrement_rel (long volatile \*) |
|_InterlockedExchange|long __cdecl _InterlockedExchange (long volatile \* _Target、long) |
|_InterlockedExchange_acq|long _InterlockedExchange_acq (long volatile \* _Target、long) |
|_InterlockedExchange_nf|long _InterlockedExchange_nf (long volatile \* _Target、long) |
|_InterlockedExchange_rel|long _InterlockedExchange_rel (long volatile \* _Target、long) |
|_InterlockedExchange16|簡短的 _InterlockedExchange16 (短 volatile \* _Target，簡短) |
|_InterlockedExchange16_acq|簡短的 _InterlockedExchange16_acq (短 volatile \* _Target，簡短) |
|_InterlockedExchange16_nf|簡短的 _InterlockedExchange16_nf (短 volatile \* _Target，簡短) |
|_InterlockedExchange16_rel|簡短的 _InterlockedExchange16_rel (短 volatile \* _Target，簡短) |
|_InterlockedExchange64|__int64 _InterlockedExchange64 (\_ _int64 volatile \* _Target， \_ _int64) |
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (\_ _int64 volatile \* _Target， \_ _int64) |
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (\_ _int64 volatile \* _Target， \_ _int64) |
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel (\_ _int64 volatile \* _Target， \_ _int64) |
|_InterlockedExchange8|char _InterlockedExchange8 (char volatile \* _Target，char) |
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char volatile \* _Target，char) |
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char volatile \* _Target，char) |
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (char volatile \* _Target，char) |
|_InterlockedExchangeAdd|long __cdecl _InterlockedExchangeAdd (long volatile \* 、long) |
|_InterlockedExchangeAdd16|簡短的 _InterlockedExchangeAdd16 (short volatile \* 、short) |
|_InterlockedExchangeAdd16_acq|簡短的 _InterlockedExchangeAdd16_acq (short volatile \* 、short) |
|_InterlockedExchangeAdd16_nf|簡短的 _InterlockedExchangeAdd16_nf (short volatile \* 、short) |
|_InterlockedExchangeAdd16_rel|簡短的 _InterlockedExchangeAdd16_rel (short volatile \* 、short) |
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8 (char volatile \* ，char) |
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq (char volatile \* ，char) |
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf (char volatile \* ，char) |
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel (char volatile \* ，char) |
|_InterlockedExchangeAdd_acq|long _InterlockedExchangeAdd_acq (long volatile \* 、long) |
|_InterlockedExchangeAdd_nf|long _InterlockedExchangeAdd_nf (long volatile \* 、long) |
|_InterlockedExchangeAdd_rel|long _InterlockedExchangeAdd_rel (long volatile \* 、long) |
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* _Target、void \*) |
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* volatile \* _Target、void \*) |
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* _Target、void \*) |
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* volatile \* _Target、void \*) |
|_InterlockedIncrement|long __cdecl _InterlockedIncrement (long volatile \*) |
|_InterlockedIncrement16|簡短 _InterlockedIncrement16 (短 volatile \*) |
|_InterlockedIncrement16_acq|簡短 _InterlockedIncrement16_acq (短 volatile \*) |
|_InterlockedIncrement16_nf|簡短 _InterlockedIncrement16_nf (短 volatile \*) |
|_InterlockedIncrement16_rel|簡短 _InterlockedIncrement16_rel (短 volatile \*) |
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 (\_ _int64 volatile \*) |
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq (\_ _int64 volatile \*) |
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf (\_ _int64 volatile \*) |
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel (\_ _int64 volatile \*) |
|_InterlockedIncrement_acq|long _InterlockedIncrement_acq (long volatile \*) |
|_InterlockedIncrement_nf|long _InterlockedIncrement_nf (long volatile \*) |
|_InterlockedIncrement_rel|long _InterlockedIncrement_rel (long volatile \*) |
|_InterlockedOr|long _InterlockedOr (long volatile \* 、long) |
|_InterlockedOr16|簡短的 _InterlockedOr16 (short volatile \* 、short) |
|_InterlockedOr16_acq|簡短的 _InterlockedOr16_acq (short volatile \* 、short) |
|_InterlockedOr16_nf|簡短的 _InterlockedOr16_nf (short volatile \* 、short) |
|_InterlockedOr16_rel|簡短的 _InterlockedOr16_rel (short volatile \* 、short) |
|_InterlockedOr64|__int64 _InterlockedOr64 (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedOr8|char _InterlockedOr8 (char volatile \* ，char) |
|_InterlockedOr8_acq|char _InterlockedOr8_acq (char volatile \* ，char) |
|_InterlockedOr8_nf|char _InterlockedOr8_nf (char volatile \* ，char) |
|_InterlockedOr8_rel|char _InterlockedOr8_rel (char volatile \* ，char) |
|_InterlockedOr_acq|long _InterlockedOr_acq (long volatile \* 、long) |
|_InterlockedOr_nf|long _InterlockedOr_nf (long volatile \* 、long) |
|_InterlockedOr_rel|long _InterlockedOr_rel (long volatile \* 、long) |
|_InterlockedXor|long _InterlockedXor (long volatile \* 、long) |
|_InterlockedXor16|簡短的 _InterlockedXor16 (short volatile \* 、short) |
|_InterlockedXor16_acq|簡短的 _InterlockedXor16_acq (short volatile \* 、short) |
|_InterlockedXor16_nf|簡短的 _InterlockedXor16_nf (short volatile \* 、short) |
|_InterlockedXor16_rel|簡短的 _InterlockedXor16_rel (short volatile \* 、short) |
|_InterlockedXor64|__int64 _InterlockedXor64 (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (\_ _int64 volatile \* ， \_ _int64) |
|_InterlockedXor8|char _InterlockedXor8 (char volatile \* ，char) |
|_InterlockedXor8_acq|char _InterlockedXor8_acq (char volatile \* ，char) |
|_InterlockedXor8_nf|char _InterlockedXor8_nf (char volatile \* ，char) |
|_InterlockedXor8_rel|char _InterlockedXor8_rel (char volatile \* ，char) |
|_InterlockedXor_acq|long _InterlockedXor_acq (long volatile \* 、long) |
|_InterlockedXor_nf|long _InterlockedXor_nf (long volatile \* 、long) |
|_InterlockedXor_rel|long _InterlockedXor_rel (long volatile \* 、long) |

[[回到頁首](#top)]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest 內建函式

一般連鎖位測試內建函式通用於所有平臺。 ARM64 會新增 `_acq` 、 `_rel` 和 `_nf` 變體，而這只會修改作業的關卡語義，如本文稍早 [ (沒有任何範圍) 尾碼的 _nf](#nf_suffix) 所述。

|函數名稱|函式原型|
|-------------------|------------------------|
|_interlockedbittestandreset|不帶正負號的 char _interlockedbittestandreset (long volatile \* 、long) |
|_interlockedbittestandreset_acq|不帶正負號的 char _interlockedbittestandreset_acq (long volatile \* 、long) |
|_interlockedbittestandreset_nf|不帶正負號的 char _interlockedbittestandreset_nf (long volatile \* 、long) |
|_interlockedbittestandreset_rel|不帶正負號的 char _interlockedbittestandreset_rel (long volatile \* 、long) |
|_interlockedbittestandreset64|不帶正負號的 char _interlockedbittestandreset64 (__int64 volatile \* ，__int64) |
|_interlockedbittestandreset64_acq|不帶正負號的 char _interlockedbittestandreset64_acq (__int64 volatile \* ，__int64) |
|_interlockedbittestandreset64_nf|不帶正負號的 char _interlockedbittestandreset64_nf (__int64 volatile \* ，__int64) |
|_interlockedbittestandreset64_rel|不帶正負號的 char _interlockedbittestandreset64_rel (__int64 volatile \* ，__int64) |
|_interlockedbittestandset|不帶正負號的 char _interlockedbittestandset (long volatile \* 、long) |
|_interlockedbittestandset_acq|不帶正負號的 char _interlockedbittestandset_acq (long volatile \* 、long) |
|_interlockedbittestandset_nf|不帶正負號的 char _interlockedbittestandset_nf (long volatile \* 、long) |
|_interlockedbittestandset_rel|不帶正負號的 char _interlockedbittestandset_rel (long volatile \* 、long) |
|_interlockedbittestandset64|不帶正負號的 char _interlockedbittestandset64 (__int64 volatile \* ，__int64) |
|_interlockedbittestandset64_acq|不帶正負號的 char _interlockedbittestandset64_acq (__int64 volatile \* ，__int64) |
|_interlockedbittestandset64_nf|不帶正負號的 char _interlockedbittestandset64_nf (__int64 volatile \* ，__int64) |
|_interlockedbittestandset64_rel|不帶正負號的 char _interlockedbittestandset64_rel (__int64 volatile \* ，__int64) |

[[回到頁首](#top)]

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[ARM 內建函式](arm-intrinsics.md)\
[ARM 組合器參考](../assembler/arm/arm-assembler-reference.md)\
[C + + 語言參考](../cpp/cpp-language-reference.md)
