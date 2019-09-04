---
title: _WriteBarrier
ms.date: 09/02/2019
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: a41f4c6c5cdd6b72e76a596622912e88fbd03f34
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219322"
---
# <a name="_writebarrier"></a>_WriteBarrier

**Microsoft 專屬**

限制可跨呼叫點，對記憶體存取作業進行重新排序的編譯器最佳化作業。

> [!CAUTION]
> `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 對於執行緒間通訊, 請使用如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)和[std:\<:](../standard-library/atomic.md)不可部分完成的[ C++ ](../standard-library/cpp-standard-library-reference.md)T > (定義于標準程式庫中) 的機制。 針對硬體存取, 請使用[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項搭配[volatile](../cpp/volatile-cpp.md)關鍵字。

## <a name="syntax"></a>語法

```C
void _WriteBarrier(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_WriteBarrier`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`_WriteBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取作業或對其進行重新排序的編譯器最佳化作業。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_ReadBarrier](../intrinsics/readbarrier.md)\
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)\
[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
