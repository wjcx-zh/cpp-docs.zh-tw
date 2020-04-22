---
title: ARM64 內建
description: Microsoft C++編譯器在 Visual Studio 中支援的 ARM64 內部函數的參考清單。
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
ms.openlocfilehash: 27325df55d128337a45e76bbf5387508a523f57c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754516"
---
# <a name="arm64-intrinsics"></a>ARM64 內建

Microsoft C++編譯器 (MSVC) 在 ARM64 體系結構上提供了以下內部函數。 有關 ARM 的詳細資訊,請參閱[ARM 開發人員文檔](https://developer.arm.com/docs)網站的體系結構和軟體開發工具部分。

## <a name="neon"></a><a name="top"></a>霓虹燈

ARM64 的 NEON 向量指令集擴展提供單指令多數據 (SIMD) 功能。 它們類似於 MMX 和 SSE 向量指令集中中 x86 和 x64 體系結構處理器中常見的指令集。

NEON 內部函數受支援,如標頭檔*arm64_neon.h*中提供。 對 NEON 內部函數的 MSVC 支援類似於 ARM64 編譯器的支援,該編譯器記錄在 ARM 資訊中心網站上的[ARM NEON 內部參考](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf)中。

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a>ARM64 特定內部函數清單

|函數名稱|指令|函式原型|
|-------------------|-----------------|------------------------|
|__break|BRK|空白__break(int)|
|__addx18byte||無效__addx18byte(無符號長,無符號字元)|
|__addx18word||無效__addx18word(無符號長,無符號短)|
|__addx18dword||無效__addx18dword(無符號長,無符號長)|
|__addx18qword||無效__addx18qword(無符號長,無符號__int64)|
|__cas8|CASB|未簽署__int8__cas8(未簽署__int8易失性* _Target、未簽名__int8_Comp、未簽名__int8_Value)|
|__cas16|現金|無符號__int16__cas16(無符號__int16易失性* _Target,無符號__int16_Comp,未簽名__int16_Value)|
|__cas32|CAS|無符號__int32__cas32(無符號__int32易失_Target、無符號__int32_Comp、無符號__int32_Value)|
|__cas64|CAS|未簽名__int64__cas64(無符號__int64易失性* _Target、無符號__int64_Comp、無符號__int64_Value)|
|__casa8|CASAB|無符號__int8__casa8(無符號__int8易失性* _Target、無符號__int8_Comp、無符號__int8_Value)|
|__casa16|CASAH|未簽署__int16__casa16(無符號__int16易失性* _Target、未簽名__int16_Comp、未簽名__int16_Value)|
|__casa32|CASA|未簽名__int32__casa32(無符號__int32易失性* _Target、無符號__int32_Comp、無符號__int32_Value)|
|__casa64|CASA|未簽署__int64__casa64(無符號__int64易失性* _Target、未簽名__int64_Comp、無符號__int64_Value)|
|__casl8|CASLB|無符號__int8__casl8(無符號__int8易失性* _Target,未簽名__int8_Comp,無符號__int8_Value)|
|__casl16|CASLH|未簽署__int16__casl16(無符號__int16易失性* _Target、未簽名__int16_Comp、未簽名__int16_Value)|
|__casl32|CASL|未簽署__int32__casl32(無符號__int32易失性* _Target、未簽名__int32_Comp、無符號__int32_Value)|
|__casl64|CASL|未簽署__int64__casl64(無符號__int64易失性* _Target、未簽名__int64_Comp、無符號__int64_Value)|
|__casal8|卡薩布|未簽署__int8__casal8(無符號__int8易失性* _Target、未簽名__int8_Comp、無符號__int8_Value)|
|__casal16|卡薩勒|未簽署__int16__casal16(無符號__int16易失性* _Target、未簽名__int16_Comp、無符號__int16_Value)|
|__casal32|卡薩拉爾|未簽署__int32__casal32(無符號__int32易失性* _Target,未簽名__int32_Comp,無符號__int32_Value)|
|__casal64|卡薩拉爾|未簽名__int64__casal64(無符號__int64易失性* _Target、無符號__int64_Comp、無符號__int64_Value)|
|__crc32b|CRC32B|未簽名__int32__crc32b(未簽署__int32,無符號__int32)|
|__crc32h|CRC32H|未簽名__int32__crc32h(未簽名__int32,無符號__int32)|
|__crc32w|CRC32W|未簽名__int32__crc32w(無符號__int32,無符號__int32)|
|__crc32d|CRC32X|未簽名__int32__crc32d(未簽名__int32,無符號__int64)|
|__crc32cb|CRC32CB|未簽名__int32__crc32cb(未簽署__int32,無符號__int32)|
|__crc32ch|CRC32CH|未簽名__int32__crc32ch(未簽署__int32,未簽名__int32)|
|__crc32cw|CRC32CW|未簽名__int32__crc32cw(無符號__int32,無符號__int32)|
|__crc32cd|CRC32CX|未簽名__int32__crc32cd(未簽署__int32,未簽名__int64)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> 將記憶體屏障作業插入指令資料流中。 參數 `_Type` 會指定屏障強制執行的限制類型。<br /><br /> 有關可強制執行的限制類型的詳細資訊,請參閱[記憶體障礙限制](#BarrierRestrictions)。|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> 將記憶體屏障作業插入指令資料流中。 參數 `_Type` 會指定屏障強制執行的限制類型。<br /><br /> 有關可強制執行的限制類型的詳細資訊,請參閱[記憶體障礙限制](#BarrierRestrictions)。|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> 將記憶體屏障作業插入指令資料流中。 參數 `_Type` 會指定屏障強制執行的限制類型。<br /><br /> 有關可強制執行的限制類型的詳細資訊,請參閱[記憶體障礙限制](#BarrierRestrictions)。|
|__getReg||未簽署__int64__getReg(int)|
|__getRegFp||雙__getRegFp(int)|
|__getCallerReg||未簽署__int64__getCallerReg(int)|
|__getCallerRegFp||雙__getCallerRegFp(int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt(無符號 int,...)|
|__incx18byte||不合法__incx18byte(無符號長)|
|__incx18word||不合法__incx18word(無符號長)|
|__incx18dword||不合法__incx18dword(無符號長)|
|__incx18qword||空白__incx18qword(無符號長)|
|__iso_volatile_load16||__int16_iso_volatile_load16(\_\_波動\*_int16 )<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__iso_volatile_load32||__int32_iso_volatile_load32(\_\_波動\*_int32 )<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__iso_volatile_load64||__int64_iso_volatile_load64(\_\_波動\*_int64)<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__iso_volatile_load8||__int8_iso_volatile_load8(\_\_波動\*_int8 )<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__iso_volatile_store16||空__iso_volatile_store16(易\_\*揮 _int16,_int16) \_<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__iso_volatile_store32||空__iso_volatile_store32(易\_\*揮_int32_int32) \_<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__iso_volatile_store64||空__iso_volatile_store64(易\_\*揮_int64,_int64) \_<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__iso_volatile_store8||空__iso_volatile_store8(揮\_\*發\_性 _int8,_int8)<br /><br /> 有關詳細資訊,請參閱[__iso_volatile_load/ 儲存內部函數](#IsoVolatileLoadStore)。|
|__ldar8|LDARB|未簽署__int8__ldar8(未簽署__int8易失性* _Target)|
|__ldar16|LDARH|無符號__int16__ldar16(無符號__int16易失性* _Target)|
|__ldar32|LDAR|未簽署__int32__ldar32(未簽署__int32易失性* _Target)|
|__ldar64|LDAR|未簽署__int64__ldar64(未簽署__int64易失性* _Target)|
|__ldapr8|LDAPRB|未簽署__int8__ldapr8(未簽署__int8易失性* _Target)|
|__ldapr16|LDAPRH|無符號__int16__ldapr16(無符號__int16易失性* _Target)|
|__ldapr32|LDAPR|未簽署__int32__ldapr32(未簽署__int32易失性* _Target)|
|__ldapr64|LDAPR|未簽署__int64__ldapr64(無符號__int64易失性* _Target)|
|__mulh||\__int64__mulh(_int64、_int64)\_ \_|
|__prefetch|PRFM|_prefetch__cdecl\_空白 (\*空白 )<br /><br /> 向`PRFM`系統提供記憶體提示,其中預取`PLDL1KEEP`操作表明,可能很快就會訪問指定位址或附近的記憶體。 有些系統可能會選擇最佳化此記憶體存取模式，來增加執行階段效能。 不過，從 C++ 語言的觀點來看，函式沒有顯著的影響，而且可能根本不執行任何動作。|
|__prefetch2|PRFM|空__cdecl_prefetch(\_\*空白 ,uint8_t普 )<br /><br /> 向`PRFM`系統提供具有提供的預取操作的記憶體提示,以便很快可以訪問指定位址或附近的記憶體。 有些系統可能會選擇最佳化此記憶體存取模式，來增加執行階段效能。 不過，從 C++ 語言的觀點來看，函式沒有顯著的影響，而且可能根本不執行任何動作。|
|__readx18byte||無符號__readx18byte( 未簽署 )|
|__readx18word||無符號短__readx18word(無符號長)|
|__readx18dword||無符號長__readx18dword(無符號長)|
|__readx18qword||未簽署__int64__readx18qword(無符號長)|
|__setReg||不__setReg合法 (無符號__int64)|
|__setRegFp||空__setRegFp(int,雙)|
|__setCallerReg||不__setCallerReg合法 (無符號__int64)|
|__setCallerRegFp||空__setCallerRegFp(int,雙)|
|__sev|SEV|void __sev(void)|
|__static_assert||空__static_assert(int,const \*char)|
|__stlr8|STLRB|無效__stlr8(無符號__int8易失性* _Target,無符號__int8_Value)|
|__stlr16|STLRH|無效__stlr16(無符號__int16易失性* _Target,無符號__int16_Value)|
|__stlr32|STLR|無效__stlr32(無符號__int32易失性* _Target,無符號__int32_Value)|
|__stlr64|STLR|無效__stlr64(無符號__int64易失性* _Target,無符號__int64_Value)|
|__swp8|SWPB|未簽署__int8__swp8(無符號__int8易失性* _Target,無符號__int8_Value)|
|__swp16|SWPH|未簽名__int16__swp16(未簽名__int16易失性* _Target,無符號__int16_Value)|
|__swp32|SWP|無符號__int32__swp32(無符號__int32易失性* _Target,無符號__int32_Value)|
|__swp64|SWP|未簽名__int64__swp64(無符號__int64易失性* _Target,無符號__int64_Value)|
|__swpa8|SWPAB|未簽署__int8__swpa8(無符號__int8易失性* _Target,無符號__int8_Value)|
|__swpa16|SWPAH|未簽名__int16__swpa16(無符號__int16易失性* _Target,無符號__int16_Value)|
|__swpa32|SWPA|未簽名__int32__swpa32(無符號__int32易失性* _Target,無符號__int32_Value)|
|__swpa64|SWPA|無符號__int64__swpa64(無符號__int64易失性* _Target,無符號__int64_Value)|
|__swpl8|SWPLB|無符號__int8__swpl8(無符號__int8易失性* _Target,無符號__int8_Value)|
|__swpl16|SWPLH|未簽署__int16__swpl16(無符號__int16易失性* _Target,無符號__int16_Value)|
|__swpl32|SWPL|未簽名__int32__swpl32(無符號__int32易失性* _Target,無符號__int32_Value)|
|__swpl64|SWPL|無符號__int64__swpl64(無符號__int64易失性* _Target,無符號__int64_Value)|
|__swpal8|SWPALB|無符號__int8__swpal8(無符號__int8易失性* _Target,無符號__int8_Value)|
|__swpal16|SWPALH|未簽名__int16__swpal16(無符號__int16易失性* _Target,無符號__int16_Value)|
|__swpal32|SWPAL|未簽名__int32__swpal32(無符號__int32易失性* _Target,無符號__int32_Value)|
|__swpal64|SWPAL|無符號__int64__swpal64(無符號__int64易失性* _Target,無符號__int64_Value)|
|__sys|SYS|無符號__sys(int,__int64)|
|__svc|SVC|無符號的int__svc(無符號int,...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||無效__writex18byte(無符號長,無符號字元)|
|__writex18word||無效__writex18word(無符號長,無符號短)|
|__writex18dword||無效__writex18dword(無符號長,無符號長)|
|__writex18qword||無效__writex18qword(無符號長,無符號__int64)|
|__umulh||未簽署\__int64__umulh(未\_簽署 _int64,\_未簽名 _int64)|
|_CopyDoubleFromInt64||雙_CopyDoubleFromInt64(_int64)\_|
|_CopyFloatFromInt32||浮_CopyFloatFromInt32(_int32)\_|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||無符號_CountLeadingOnes64(無符號\__int64)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||無符號_CountLeadingSigns64(_int64)\_|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||無符號的int_CountLeadingZeros64(無\_符號_int64)|
|_ReadStatusReg|MRS|\__int64_ReadStatusReg(國際)|
|_WriteStatusReg|MSR|空_WriteStatusReg(因,_int64) \_|

【[返回頂部](#top)】

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a>記憶體障礙限制

內部函數`__dmb`(資料記憶體屏障)、(`__dsb`資料同步屏障)`__isb`和 (指令同步障礙)使用以下預定義值在共用域和受操作影響的存取類型方面指定記憶體障礙限制。

|限制值|描述|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|完整系統，讀取和寫入。|
|_ARM64_BARRIER_ST|完整系統，只寫入。|
|_ARM64_BARRIER_LD|完整系統,只讀。|
|_ARM64_BARRIER_ISH|可內部共用，讀取和寫入。|
|_ARM64_BARRIER_ISHST|可內部共用，只寫入。|
|_ARM64_BARRIER_ISHLD|內部可共用,唯讀。|
|_ARM64_BARRIER_NSH|不可共用，讀取和寫入。|
|_ARM64_BARRIER_NSHST|不可共用，只寫入。|
|_ARM64_BARRIER_NSHLD|不可共用,唯讀。|
|_ARM64_BARRIER_OSH|可外部共用，讀取和寫入。|
|_ARM64_BARRIER_OSHST|可外部共用，只寫入。|
|_ARM64_BARRIER_OSHLD|外可共用,只讀。|

對於`__isb`內部,當前唯一有效的限制是_ARM64_BARRIER_SY;所有其他值由體系結構保留。

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a>__iso_volatile_load/儲存內部

這些內部函數顯式執行不受編譯器優化約束的負載和存儲。

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

*價值*\
要寫入指定記憶體位置的值(僅存儲內部函數)。

#### <a name="return-value-load-intrinsics-only"></a>傳回值(僅載入內部函式)

由*位置*指定的記憶體位置的值。

#### <a name="remarks"></a>備註

可以使用和`__iso_volatile_load8/16/32/64``__iso_volatile_store8/16/32/64`內部函數顯式執行不受編譯器優化約束的記憶體訪問。 編譯器無法刪除、合成或更改這些操作的相對順序。 但是,它不會生成隱式硬體記憶體障礙。 因此，硬體可能仍然重新排列跨多個執行緒中可觀察到的記憶體存取。 更確切地說,這些內在函數等效於以下表達式,這些運算式在 **/volatile:iso**下編譯。

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

請注意，內建函式採取暫時性 (volatile) 指標以容納暫時性變數。 但是,沒有要求或建議使用易失性指標作為參數。 如果使用常規非易失性類型,則這些操作的語義完全相同。

有關 **/volatile:iso**命令列參數的詳細資訊,請參閱[/volatile(易失性關鍵字解釋)。](../build/reference/volatile-volatile-keyword-interpretation.md)

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a>ARM64 支援其他體系結構的固有產品

下表列出了 ARM64 平臺上支援的其他體系結構的固有函數。 如果 ARM64 上的內在行為不同於其他硬體體系結構上的行為,則請注意其他詳細資訊。

|函數名稱|函式原型|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|空白__code_seg(康斯特字元\*)|
|__debugbreak|不合法__cdecl_debugbreak(\_空白 )|
|__fastfail|__declspec(無返回)無效\__fastfail(無符號int)|
|__nop|void __nop(void)|
|__yield|無效__yield(無效)**注意:** 在 ARM64 平臺上,此功能生成 YIELD 指令。 此指令指示線程正在執行可能暫時暫停執行的任務(例如,旋轉鎖),而不會對程序產生負面影響。 它使 CPU 能夠在執行週期內執行其他任務,否則這些任務會浪費。|
|_AddressOfReturnAddress|空\*_AddressOfReturnAddress(空)|
|_BitScanForward|無符號字元_BitScanForward(未簽名的長\*_Index,未簽名長_Mask)|
|_BitScanForward64|無符號字元_BitScanForward64(未簽名長\*_Index,無符號__int64_Mask)|
|_BitScanReverse|無符號字元_BitScanReverse(無符號長\*_Index,無符號長_Mask)|
|_BitScanReverse64|無符號字元_BitScanReverse64(未簽署的長\*_Index,無符號__int64_Mask)|
|_bittest|無符號字元_bittest(長孔\*,長)|
|_bittest64|無符號字元\*_bittest64(__int64,__int64)|
|_bittestandcomplement|無符號字元_bittestandcomplement(長\*,長)|
|_bittestandcomplement64|無符號字元_bittestandcomplement64(__int64,__int64) \*|
|_bittestandreset|無符號字元_bittestandreset(長\*,長)|
|_bittestandreset64|無符號字元_bittestandreset64(__int64,__int64) \*|
|_bittestandset|無符號字元_bittestandset(長\*,長)|
|_bittestandset64|無符號字元_bittestandset64(__int64,__int64) \*|
|_byteswap_uint64|未簽署__int64_cdecl_byteswap_uint64(\_未\_簽署 _int64 )|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|無效__cdecl_disable(不合法)**注意:** 在 ARM64 平臺上`MSR DAIFCLR,#2`,此功能產生指令 ;它只能作為一種內在的。|
|_enable|空__cdecl_enable(不合法)**注意:** 在 ARM64 平臺上`MSR DAIFSET,#2`,此功能產生指令 ;它只能作為一種內在的。|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|空\*_ReturnAddress(空)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|未簽署__int64_cdecl_rotl64(\_未\_簽署 _int64_Value,_Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|未簽署__int64_cdecl_rotr64(\_未\_簽署 _int64_Value,_Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

【[返回頂部](#top)】

## <a name="interlocked-intrinsics"></a>互鎖內部

連鎖內建函式是一組內建函式，用來執行不可部分完成的讀取-修改-寫入作業。 其中有部分通用於所有平台。 它們在此處單獨列出,因為存在大量。 因為它們的定義大多是多餘的,因此更容易從一般角度考慮它們。 它們的名稱可以用來得出確切的行為。

下表總結了 ARM64 對非位測試互鎖內部項的支援。 在表中的每個儲存格對應的名稱，是將列的最左邊儲存格的作業名稱，和欄的最上方儲存格的類型名稱，附加至 `_Interlocked` 所衍生的名稱。 例如,`Xor`行`8`和 列交集處的單元格`_InterlockedXor8`對應於 並完全支援。 大部分受支援的函式會提供這些選擇性的字尾：`_acq`、`_rel` 和 `_nf`。 `_acq` 字尾表示「取得」語意，`_rel` 字尾表示「釋放」語意。 或`_nf`「無柵欄」後綴是 ARM 和 ARM64 獨有的,在下一節中將對此進行討論。

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|加|None|None|完整|完整|None|None|
|And|完整|完整|完整|完整|None|None|
|CompareExchange|完整|完整|完整|完整|完整|完整|
|遞減|None|完整|完整|完整|None|None|
|Exchange|完整|完整|完整|完整|None|完整|
|ExchangeAdd|完整|完整|完整|完整|None|None|
|[遞增]|None|完整|完整|完整|None|None|
|Or|完整|完整|完整|完整|None|None|
|Xor|完整|完整|完整|完整|None|None|

機碼：

- **完整**:`_acq``_rel`支援 普通`_nf`、、和表單。

- **沒有**: 不支援

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a>_nf(無柵欄)後綴

或`_nf`"無柵欄"後綴表示操作不作為任何類型的記憶體屏障,與其他三種形式(普通、`_acq``_rel`和 )不同,它們都作為某種屏障運行。 `_nf`窗體的一個可能用途是維護一個統計計數器,該計數器同時由多個線程更新,但在多個線程執行時,其值未以其他方式使用。

### <a name="list-of-interlocked-intrinsics"></a>互鎖內部函式清單

|函數名稱|函式原型|
|-------------------|------------------------|
|_InterlockedAdd|長_InterlockedAdd(長_volatile\*長)|
|_InterlockedAdd64|__int64_InterlockedAdd64(_int64\_\*波動 ,_int64) \_|
|_InterlockedAdd64_acq|__int64_InterlockedAdd64_acq(_int64\_\*波動 ,_int64) \_|
|_InterlockedAdd64_nf|__int64_InterlockedAdd64_nf(_int64\_\*波動 ,_int64) \_|
|_InterlockedAdd64_rel|__int64_InterlockedAdd64_rel(_int64\_\*波動 ,_int64) \_|
|_InterlockedAdd_acq|長_InterlockedAdd_acq(長時間揮\*發性,長)|
|_InterlockedAdd_nf|長_InterlockedAdd_nf(長時間揮\*發性,長)|
|_InterlockedAdd_rel|長_InterlockedAdd_rel(長時間揮\*發性,長)|
|_InterlockedAnd|長_InterlockedAnd(長時間揮\*發性,長)|
|_InterlockedAnd16|短_InterlockedAnd16(短波動\*、短)|
|_InterlockedAnd16_acq|短_InterlockedAnd16_acq(短波動\*、短)|
|_InterlockedAnd16_nf|短_InterlockedAnd16_nf(短波動\*、短)|
|_InterlockedAnd16_rel|空_InterlockedAnd16_rel(短波動\*、短)|
|_InterlockedAnd64|__int64_InterlockedAnd64(_int64\_\*波動 ,_int64) \_|
|_InterlockedAnd64_acq|__int64_InterlockedAnd64_acq(_int64\_\*波動 ,_int64) \_|
|_InterlockedAnd64_nf|__int64_InterlockedAnd64_nf(_int64\_\*波動 ,_int64) \_|
|_InterlockedAnd64_rel|__int64_InterlockedAnd64_rel(_int64\_\*波動 ,_int64) \_|
|_InterlockedAnd8|字元_InterlockedAnd8 (字\*元 易揮發 , 字元)|
|_InterlockedAnd8_acq|字元_InterlockedAnd8_acq (字\*元 易揮發 , 字元)|
|_InterlockedAnd8_nf|字元_InterlockedAnd8_nf (字\*元 易揮發 , 字元)|
|_InterlockedAnd8_rel|字元_InterlockedAnd8_rel (字\*元 易揮發 , 字元)|
|_InterlockedAnd_acq|長_InterlockedAnd_acq(長揮\*發性,長)|
|_InterlockedAnd_nf|長_InterlockedAnd_nf(長時間揮\*發性,長)|
|_InterlockedAnd_rel|長_InterlockedAnd_rel(長時間揮\*發性,長)|
|_InterlockedCompareExchange|長__cdecl_InterlockedCompareExchange(長揮\*發、長、長)|
|_InterlockedCompareExchange_acq|長_InterlockedCompareExchange_acq(長揮\*發、長、長)|
|_InterlockedCompareExchange_nf|長_InterlockedCompareExchange_nf(長揮\*發、長、長)|
|_InterlockedCompareExchange_rel|長_InterlockedCompareExchange_rel(長揮\*發、長、長)|
|_InterlockedCompareExchange16|短_InterlockedCompareExchange16(短波動\*、短、短)|
|_InterlockedCompareExchange16_acq|短_InterlockedCompareExchange16_acq(短波動\*、短、短)|
|_InterlockedCompareExchange16_nf|短_InterlockedCompareExchange16_nf(短波動\*、短、短)|
|_InterlockedCompareExchange16_rel|短_InterlockedCompareExchange16_rel(短波動\*、短、短)|
|_InterlockedCompareExchange64|__int64_InterlockedCompareExchange64(_int64\_波動\*、_int64、_int64) \_ \_|
|_InterlockedCompareExchange64_acq|__int64_InterlockedCompareExchange64_acq(_int64\_波動\*、_int64、_int64) \_ \_|
|_InterlockedCompareExchange64_nf|__int64_InterlockedCompareExchange64_nf(_int64\_\*波動 、_int64、_int64) \_ \_|
|_InterlockedCompareExchange64_rel|__int64_InterlockedCompareExchange64_rel(_int64\_波動\*、_int64、_int64) \_ \_|
|_InterlockedCompareExchange8|字元_InterlockedCompareExchange8 (字\*元 易揮發, 字元, 字元)|
|_InterlockedCompareExchange8_acq|字元_InterlockedCompareExchange8_acq (字\*元 易揮發, 字元, 字元)|
|_InterlockedCompareExchange8_nf|字元_InterlockedCompareExchange8_nf(字元揮\*發性,字元,字元)|
|_InterlockedCompareExchange8_rel|字元_InterlockedCompareExchange8_rel(字元揮\*發性,字元,字元)|
|_InterlockedCompareExchangePointer|空\*_InterlockedCompareExchangePointer(\*空\*揮\*發\*、 空隙、空)|
|_InterlockedCompareExchangePointer_acq|空\*_InterlockedCompareExchangePointer_acq(\*空\*揮\*發\*、 空隙、空)|
|_InterlockedCompareExchangePointer_nf|空\*_InterlockedCompareExchangePointer_nf(\*空\*揮\*發\*、 空隙、空)|
|_InterlockedCompareExchangePointer_rel|空\*_InterlockedCompareExchangePointer_rel(\*空\*揮\*發\*、 空隙、空)|
|_InterlockedCompareExchange128|\_無符號字元_InterlockedCompareExchange128(_int64volatile \* _Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult) \_ \_ \_ \*|
|_InterlockedCompareExchange128_acq|\_無符號字元_InterlockedCompareExchange128_acq(_int64volatile \* _Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult) \_ \_ \_ \*|
|_InterlockedCompareExchange128_nf|無符號字元_InterlockedCompareExchange128_nf(_int64\_\*易 變_Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult) \_ \_ \_ \*|
|_InterlockedCompareExchange128_rel|\_無符號字元_InterlockedCompareExchange128_rel(_int64volatile \* _Destination、_int64_ExchangeHigh、_int64_ExchangeLow、_int64_ComparandResult) \_ \_ \_ \*|
|_InterlockedDecrement|長__cdecl_InterlockedDecrement(長時間揮\*發)|
|_InterlockedDecrement16|短_InterlockedDecrement16(短揮\*發性)|
|_InterlockedDecrement16_acq|短_InterlockedDecrement16_acq(短揮\*發性)|
|_InterlockedDecrement16_nf|短_InterlockedDecrement16_nf(短波動\*)|
|_InterlockedDecrement16_rel|短_InterlockedDecrement16_rel(短揮\*發性)|
|_InterlockedDecrement64|__int64_InterlockedDecrement64(_int64\_波動\*)|
|_InterlockedDecrement64_acq|__int64_InterlockedDecrement64_acq(_int64\_波動\*)|
|_InterlockedDecrement64_nf|__int64_InterlockedDecrement64_nf(_int64\_波動\*)|
|_InterlockedDecrement64_rel|__int64_InterlockedDecrement64_rel(_int64\_\*波動 )|
|_InterlockedDecrement_acq|長_InterlockedDecrement_acq(長時間揮\*發)|
|_InterlockedDecrement_nf|長_InterlockedDecrement_nf(長時間揮\*發)|
|_InterlockedDecrement_rel|長_InterlockedDecrement_rel(長時間揮\*發)|
|_InterlockedExchange|長__cdecl_InterlockedExchange(長揮\*發_Target,長)|
|_InterlockedExchange_acq|長_InterlockedExchange_acq(長揮\*發_Target,長)|
|_InterlockedExchange_nf|長_InterlockedExchange_nf(長揮\*發_Target,長)|
|_InterlockedExchange_rel|長_InterlockedExchange_rel(長揮\*發_Target,長)|
|_InterlockedExchange16|短_InterlockedExchange16(短波動\*_Target,短)|
|_InterlockedExchange16_acq|短_InterlockedExchange16_acq(短波動\*_Target,短)|
|_InterlockedExchange16_nf|短_InterlockedExchange16_nf(短波動\*_Target,短)|
|_InterlockedExchange16_rel|短_InterlockedExchange16_rel(短波動\*_Target,短)|
|_InterlockedExchange64|__int64_InterlockedExchange64(_int64\_\*波動 _Target,_int64) \_|
|_InterlockedExchange64_acq|__int64_InterlockedExchange64_acq(_int64\_波動\*_Target,_int64) \_|
|_InterlockedExchange64_nf|\___int64_InterlockedExchange64_nf(_int64_Target\*波動,_int64) \_|
|_InterlockedExchange64_rel|\___int64_InterlockedExchange64_rel(_int64_Target\*波動,_int64) \_|
|_InterlockedExchange8|字元_InterlockedExchange8(炭易\*揮發_Target,字元)|
|_InterlockedExchange8_acq|字元_InterlockedExchange8_acq(字元揮\*發性_Target,字元)|
|_InterlockedExchange8_nf|字元_InterlockedExchange8_nf(字元易\*失性_Target,字元)|
|_InterlockedExchange8_rel|字元_InterlockedExchange8_rel(炭易\*失性_Target,字元)|
|_InterlockedExchangeAdd|長__cdecl_InterlockedExchangeAdd(長時間揮\*髮,長)|
|_InterlockedExchangeAdd16|短_InterlockedExchangeAdd16(短波動\*、短)|
|_InterlockedExchangeAdd16_acq|短_InterlockedExchangeAdd16_acq(短波動\*、短)|
|_InterlockedExchangeAdd16_nf|短_InterlockedExchangeAdd16_nf(短波動\*、短)|
|_InterlockedExchangeAdd16_rel|短_InterlockedExchangeAdd16_rel(短波動\*、短)|
|_InterlockedExchangeAdd64|__int64_InterlockedExchangeAdd64(_int64\_\*波動 ,_int64) \_|
|_InterlockedExchangeAdd64_acq|__int64_InterlockedExchangeAdd64_acq(_int64\_\*波動 ,_int64) \_|
|_InterlockedExchangeAdd64_nf|__int64_InterlockedExchangeAdd64_nf(_int64\_\*波動 ,_int64) \_|
|_InterlockedExchangeAdd64_rel|__int64_InterlockedExchangeAdd64_rel(_int64\_\*波動 ,_int64) \_|
|_InterlockedExchangeAdd8|字元_InterlockedExchangeAdd8 (字\*元 易失性, 字元 )|
|_InterlockedExchangeAdd8_acq|字元_InterlockedExchangeAdd8_acq (字\*元 易揮發 , 字元)|
|_InterlockedExchangeAdd8_nf|字元_InterlockedExchangeAdd8_nf (字\*元 易揮發 , 字元)|
|_InterlockedExchangeAdd8_rel|字元_InterlockedExchangeAdd8_rel (字\*元 易揮發 , 字元)|
|_InterlockedExchangeAdd_acq|長_InterlockedExchangeAdd_acq(長揮\*發性,長)|
|_InterlockedExchangeAdd_nf|長_InterlockedExchangeAdd_nf(長時間揮\*發性,長)|
|_InterlockedExchangeAdd_rel|長_InterlockedExchangeAdd_rel(長時間揮\*發性,長)|
|_InterlockedExchangePointer|空\*_InterlockedExchangePointer(\*空\*揮\*發_Target, 空)|
|_InterlockedExchangePointer_acq|空\*_InterlockedExchangePointer_acq(\*空\*揮\*發_Target, 空)|
|_InterlockedExchangePointer_nf|空\*_InterlockedExchangePointer_nf(\*空\*揮\*發_Target, 空)|
|_InterlockedExchangePointer_rel|空\*_InterlockedExchangePointer_rel(真\*空\*揮\*發_Target, 空)|
|_InterlockedIncrement|長__cdecl_InterlockedIncrement(長時間揮\*發)|
|_InterlockedIncrement16|短_InterlockedIncrement16(短波動\*)|
|_InterlockedIncrement16_acq|短_InterlockedIncrement16_acq(短揮\*發性)|
|_InterlockedIncrement16_nf|短_InterlockedIncrement16_nf(短波動\*)|
|_InterlockedIncrement16_rel|短_InterlockedIncrement16_rel(短揮\*發性)|
|_InterlockedIncrement64|__int64_InterlockedIncrement64(_int64\_波動\*)|
|_InterlockedIncrement64_acq|__int64_InterlockedIncrement64_acq(_int64\_波動\*)|
|_InterlockedIncrement64_nf|__int64_InterlockedIncrement64_nf(_int64\_波動\*)|
|_InterlockedIncrement64_rel|__int64_InterlockedIncrement64_rel\_(_int64\*波動 )|
|_InterlockedIncrement_acq|長_InterlockedIncrement_acq(長時間揮\*發)|
|_InterlockedIncrement_nf|長_InterlockedIncrement_nf(長時間揮\*發)|
|_InterlockedIncrement_rel|長_InterlockedIncrement_rel(長時間揮\*發)|
|_InterlockedOr|長_InterlockedOr(長時間揮\*發性,長)|
|_InterlockedOr16|短_InterlockedOr16(短波動\*、短)|
|_InterlockedOr16_acq|短_InterlockedOr16_acq(短波動\*、短)|
|_InterlockedOr16_nf|短_InterlockedOr16_nf(短波動\*、短)|
|_InterlockedOr16_rel|短_InterlockedOr16_rel(短波動\*、短)|
|_InterlockedOr64|__int64_InterlockedOr64(_int64\_\*波動 ,_int64) \_|
|_InterlockedOr64_acq|__int64_InterlockedOr64_acq(_int64\_\*波動 ,_int64) \_|
|_InterlockedOr64_nf|__int64_InterlockedOr64_nf(_int64\_\*波動 ,_int64) \_|
|_InterlockedOr64_rel|__int64_InterlockedOr64_rel(_int64\_\*波動 ,_int64) \_|
|_InterlockedOr8|字元_InterlockedOr8 (字\*元 易揮發 , 字元)|
|_InterlockedOr8_acq|字元_InterlockedOr8_acq (字\*元 易揮發 , 字元)|
|_InterlockedOr8_nf|字元_InterlockedOr8_nf (字\*元 易揮發 , 字元)|
|_InterlockedOr8_rel|字元_InterlockedOr8_rel (字\*元 易失性, 字元 )|
|_InterlockedOr_acq|長_InterlockedOr_acq(長時間揮\*發性,長)|
|_InterlockedOr_nf|長_InterlockedOr_nf(長時間揮\*發性,長)|
|_InterlockedOr_rel|長_InterlockedOr_rel(長時間揮\*發性,長)|
|_InterlockedXor|長_InterlockedXor(長時間揮\*發性,長)|
|_InterlockedXor16|短_InterlockedXor16(短波動\*、短)|
|_InterlockedXor16_acq|空_InterlockedXor16_acq(短波動\*、短)|
|_InterlockedXor16_nf|短_InterlockedXor16_nf(短波動\*、短)|
|_InterlockedXor16_rel|短_InterlockedXor16_rel(短波動\*、短)|
|_InterlockedXor64|__int64_InterlockedXor64(_int64\_波動\*,_int64) \_|
|_InterlockedXor64_acq|__int64_InterlockedXor64_acq(_int64\_波動\*,_int64) \_|
|_InterlockedXor64_nf|__int64_InterlockedXor64_nf(_int64\_\*波動 ,_int64) \_|
|_InterlockedXor64_rel|__int64_InterlockedXor64_rel(_int64\_\*波動 ,_int64) \_|
|_InterlockedXor8|字元_InterlockedXor8 (字\*元 易揮發 , 字元)|
|_InterlockedXor8_acq|字元_InterlockedXor8_acq (字\*元 易揮發 , 字元)|
|_InterlockedXor8_nf|字元_InterlockedXor8_nf (字\*元 易揮發 , 字元)|
|_InterlockedXor8_rel|字元_InterlockedXor8_rel (字\*元 易揮發 , 字元)|
|_InterlockedXor_acq|長_InterlockedXor_acq(長時間揮\*發性,長)|
|_InterlockedXor_nf|長_InterlockedXor_nf(長時間揮\*發性,長)|
|_InterlockedXor_rel|長_InterlockedXor_rel(長時間揮\*發性,長)|

【[返回頂部](#top)】

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest內在

純聯鎖位測試內部函數是所有平臺都通用的。 ARM64`_acq`添加`_rel`了`_nf`, 和變體,它們只是修改操作的屏障語義,如本文前面[_nf(無柵欄)後綴](#nf_suffix)中所述。

|函數名稱|函式原型|
|-------------------|------------------------|
|_interlockedbittestandreset|無符號字元_interlockedbittestandreset(長時間易\*揮發,長)|
|_interlockedbittestandreset_acq|無符號字元_interlockedbittestandreset_acq(長時間易\*揮發,長)|
|_interlockedbittestandreset_nf|無符號字元_interlockedbittestandreset_nf(長時間易\*揮發,長)|
|_interlockedbittestandreset_rel|無符號字元_interlockedbittestandreset_rel(長時間易\*揮發,長)|
|_interlockedbittestandreset64|無符號字元_interlockedbittestandreset64(__int64\*易變,__int64)|
|_interlockedbittestandreset64_acq|無符號字元_interlockedbittestandreset64_acq (__int64\*易變,__int64)|
|_interlockedbittestandreset64_nf|無符號字元_interlockedbittestandreset64_nf(__int64易\*變,__int64)|
|_interlockedbittestandreset64_rel|無符號字元_interlockedbittestandreset64_rel(__int64\*易變,__int64)|
|_interlockedbittestandset|無符號字元_interlockedbittestandset(長時間易\*揮發,長)|
|_interlockedbittestandset_acq|無符號字元_interlockedbittestandset_acq(長時間易\*揮發,長)|
|_interlockedbittestandset_nf|無符號字元_interlockedbittestandset_nf(長時間易\*揮發,長)|
|_interlockedbittestandset_rel|無符號字元_interlockedbittestandset_rel(長時間易\*揮發,長)|
|_interlockedbittestandset64|無符號字元_interlockedbittestandset64(__int64\*易變,__int64)|
|_interlockedbittestandset64_acq|無符號字元_interlockedbittestandset64_acq(__int64易\*變,__int64)|
|_interlockedbittestandset64_nf|無符號字元_interlockedbittestandset64_nf(__int64易\*變,__int64)|
|_interlockedbittestandset64_rel|無符號字元_interlockedbittestandset64_rel(__int64易\*變,__int64)|

【[返回頂部](#top)】

## <a name="see-also"></a>另請參閱

[編譯器內部函數](../intrinsics/compiler-intrinsics.md)\
[ARM 內部函數](arm-intrinsics.md)\
[ARM 裝接器參考](../assembler/arm/arm-assembler-reference.md)\
[C++語言參考](../cpp/cpp-language-reference.md)
