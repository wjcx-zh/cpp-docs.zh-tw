---
title: _ReadBarrier
ms.date: 09/02/2019
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: 8bbcecf95daeef6ea2d40877d37e0eb6b7f3a0e8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217091"
---
# <a name="_readbarrier"></a>_ReadBarrier

**Microsoft 專屬**

限制可跨呼叫點，對記憶體存取作業進行重新排序的編譯器最佳化作業。

> [!CAUTION]
> `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 對於執行緒間通訊, 請使用在[ C++標準程式庫](../standard-library/cpp-standard-library-reference.md)中定義的機制, 例如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)和[\<std::](../standard-library/atomic.md)不可部分完成的 T >。 針對硬體存取, 請使用[/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項搭配[volatile](../cpp/volatile-cpp.md)關鍵字。

## <a name="syntax"></a>語法

```C
void _ReadBarrier(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_ReadBarrier`|x86、x64|

**標頭檔**\<intrin.h. h >

## <a name="remarks"></a>備註

`_ReadBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取作業或對其進行重新排序的編譯器最佳化作業。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
