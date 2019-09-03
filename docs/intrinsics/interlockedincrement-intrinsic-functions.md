---
title: _InterlockedIncrement 內建函式
ms.date: 09/02/2019
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
ms.openlocfilehash: 4dd9ae9ba5454b0afefa332689d94fa3619a07a6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221980"
---
# <a name="_interlockedincrement-intrinsic-functions"></a>_InterlockedIncrement 內建函式

**Microsoft 專屬**

提供 Win32 Windows SDK [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)函數的編譯器內建支援。

## <a name="syntax"></a>語法

```C
long _InterlockedIncrement(
   long * lpAddend
);
long _InterlockedIncrement_acq(
   long * lpAddend
);
long _InterlockedIncrement_rel(
   long * lpAddend
);
long _InterlockedIncrement_nf(
   long * lpAddend
);
short _InterlockedIncrement16(
   short * lpAddend
);
short _InterlockedIncrement16_acq(
   short * lpAddend
);
short _InterlockedIncrement16_rel(
   short * lpAddend
);
short _InterlockedIncrement16_nf (
   short * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 * lpAddend
);
```

### <a name="parameters"></a>參數

*lpAddend*\
[in、out]要遞增之變數的指標。

## <a name="return-value"></a>傳回值

傳回值是所產生的遞增值。

## <a name="requirements"></a>需求

|內建|架構|標頭|
|---------------|------------------|------------|
|`_InterlockedIncrement`、 `_InterlockedIncrement16`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_InterlockedIncrement64`|ARM、x64、ARM64|\<intrin.h>|
|+`_InterlockedIncrement_acq`、`_InterlockedIncrement_rel`、`_InterlockedIncrement_nf`、`_InterlockedIncrement16_acq`、`_InterlockedIncrement16_rel`、`_InterlockedIncrement16_nf`、`_InterlockedIncrement64_acq`、`_InterlockedIncrement64_rel`、`_InterlockedIncrement64_nf`|ARM、ARM64|\<intrin.h>|

## <a name="remarks"></a>備註

在 `_InterlockedIncrement` 上有數個變化，會因所涉及的資料類型，以及是否使用處理器專用的取得或釋放語意，而有所不同。

`_InterlockedIncrement` 函式在 32 位元整數值上操作，而 `_InterlockedIncrement16` 是在 16 位元整數值上操作，`_InterlockedIncrement64` 在 64 位元整數值上操作。

在 ARM 平台上，如果您需要取得並發行語意 (例如在關鍵區段的開頭和結尾)，請使用具有 `_acq` 和 `_rel` 後置字元的內建函式。 具有`_nf` (「無範圍」) 尾碼的內建函式不會做為記憶體屏障。

`lpAddend` 參數所指向的變數必須對齊 32 位元界限；否則，這個函式會在多處理器 x86 系統與任何非 x86 系統上失敗。 如需詳細資訊, 請參閱[align](../cpp/align-cpp.md)。

Win32 函式在 `Wdm.h` 或 `Ntddk.h` 中宣告。

這些常式僅以內建函式的形式供您使用。

## <a name="example"></a>範例

如需如何使用`_InterlockedIncrement`的範例, 請參閱[_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md)。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)\
[與 x86 編譯器衝突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
