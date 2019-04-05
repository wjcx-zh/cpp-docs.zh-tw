---
title: _WriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _WriteBarrier
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
ms.openlocfilehash: d2db648c9f41bd4f773f5bf152f31cf990a75c8e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025761"
---
# <a name="writebarrier"></a>_WriteBarrier

**Microsoft 特定的**

限制可跨呼叫點，對記憶體存取作業進行重新排序的編譯器最佳化作業。

> [!CAUTION]
>  `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 對於執行緒間通訊使用機制如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)並[std:: atomic\<T >](../standard-library/atomic.md)，其定義於[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md). 對於硬體存取，請使用[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項，並搭配[volatile](../cpp/volatile-cpp.md)關鍵字。

## <a name="syntax"></a>語法

```
void _WriteBarrier(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_WriteBarrier`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`_WriteBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取作業或對其進行重新排序的編譯器最佳化作業。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_ReadWriteBarrier](../intrinsics/readwritebarrier.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)