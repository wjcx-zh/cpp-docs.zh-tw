---
title: _ReadWriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: d755d045970da01d2eee33377c1452191eac4fe2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217980"
---
# <a name="_readwritebarrier"></a>_ReadWriteBarrier

**Microsoft 專屬**

限制可跨呼叫點，對記憶體存取進行重新排序的編譯器最佳化作業。

> [!CAUTION]
> `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 對於執行緒間通訊, 請使用如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)和[std:\<:](../standard-library/atomic.md)不可部分完成的[ C++ ](../standard-library/cpp-standard-library-reference.md)T > (定義于標準程式庫中) 的機制。 針對硬體存取, 請使用[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項搭配[volatile](../cpp/volatile-cpp.md)關鍵字。

## <a name="syntax"></a>語法

```C
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_ReadWriteBarrier`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`_ReadWriteBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取或對其進行重新排序的編譯器最佳化作業。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_WriteBarrier](../intrinsics/writebarrier.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
