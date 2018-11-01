---
title: _ReadWriteBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadWriteBarrier
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
ms.openlocfilehash: a279017e57c8bf828b302940463bd0b3504f085d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626157"
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier

**Microsoft 專屬**

限制可跨呼叫點，對記憶體存取進行重新排序的編譯器最佳化作業。

> [!CAUTION]
>  `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 對於執行緒間通訊使用機制如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)並[std:: atomic\<T >](../standard-library/atomic.md)，其定義於[c + + 標準程式庫](../standard-library/cpp-standard-library-reference.md). 對於硬體存取，請使用[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項，並搭配[volatile](../cpp/volatile-cpp.md)關鍵字。

## <a name="syntax"></a>語法

```
void _ReadWriteBarrier(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_ReadWriteBarrier`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`_ReadWriteBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取或對其進行重新排序的編譯器最佳化作業。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_ReadBarrier](../intrinsics/readbarrier.md)<br/>
[_WriteBarrier](../intrinsics/writebarrier.md)<br/>
[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)