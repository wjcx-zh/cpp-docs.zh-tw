---
title: _ReadBarrier
ms.date: 11/04/2016
f1_keywords:
- _ReadBarrier
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
ms.openlocfilehash: f31293b2bef0304bcdc58f0a8dbfce0436df9843
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025482"
---
# <a name="readbarrier"></a>_ReadBarrier

**Microsoft 專屬**

限制可跨呼叫點，對記憶體存取作業進行重新排序的編譯器最佳化作業。

> [!CAUTION]
>  `_ReadBarrier`、`_WriteBarrier` 和 `_ReadWriteBarrier` 編譯器內建物件及`MemoryBarrier` 巨集全部都已被取代，不應該再使用。 對於執行緒間通訊使用機制如[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)並[std:: atomic\<T >](../standard-library/atomic.md)中定義的[ C++ 的標準程式庫](../standard-library/cpp-standard-library-reference.md). 對於硬體存取，請使用[/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)編譯器選項，並搭配[volatile](../cpp/volatile-cpp.md)關鍵字。

## <a name="syntax"></a>語法

```
void _ReadBarrier(void);
```

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|`_ReadBarrier`|x86、x64|

**標頭檔** \<intrin.h >

## <a name="remarks"></a>備註

`_ReadBarrier` 內建物件會限制可跨呼叫點，移除記憶體存取作業或對其進行重新排序的編譯器最佳化作業。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)