---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 7b573127518969accdfdcc4a25a50269dd6aa002
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456393"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

_ITERATOR_DEBUG_LEVEL 宏可控制是否啟用[已檢查的反覆運算](../standard-library/checked-iterators.md)[器和 DEBUG ITERATOR 支援](../standard-library/debug-iterator-support.md)。 這個宏會取代並結合舊版 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 宏的功能。

## <a name="macro-values"></a>巨集值

下表摘要說明 _ITERATOR_DEBUG_LEVEL 宏的可能值。

|編譯模式|巨集值|說明|
|----------------------|----------------|-----------------|
|**偵錯**|||
||0|停用已檢查的迭代器及停用迭代器偵錯功能。|
||1|啟用已檢查的迭代器，但停用迭代器偵錯功能。|
||2 (預設)|停用迭代器偵錯功能；與已檢查的迭代器無關。|
|**發行**|||
||0 (預設)|停用已檢查的迭代器。|
||1|啟用已檢查的迭代器；與迭代器偵錯功能無關。|

在發行模式中, 如果您將 _ITERATOR_DEBUG_LEVEL 指定為 2, 編譯器會產生錯誤。

## <a name="remarks"></a>備註

_ITERATOR_DEBUG_LEVEL 宏可控制是否啟用[已檢查的反覆運算](../standard-library/checked-iterators.md)器, 以及在 debug 模式中是否已啟用[debug ITERATOR 支援](../standard-library/debug-iterator-support.md)。 如果 _ITERATOR_DEBUG_LEVEL 定義為1或 2, 則已檢查的反覆運算器可確保不會覆寫容器的界限。 如果 _ITERATOR_DEBUG_LEVEL 為 0, 則不會檢查反覆運算器。 當 _ITERATOR_DEBUG_LEVEL 定義為1時, 任何不安全的反覆運算器使用會導致執行階段錯誤, 而且程式會終止。 當 _ITERATOR_DEBUG_LEVEL 定義為2時, 不安全的反覆運算器使用會導致判斷提示和執行時間錯誤對話方塊, 讓您中斷偵錯工具。

由於 _ITERATOR_DEBUG_LEVEL 宏支援 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 宏的類似功能, 因此您可能不確定在特定情況下要使用哪個宏和宏值。 為了避免混淆, 我們建議您只使用 _ITERATOR_DEBUG_LEVEL 宏。 下表描述在現有程式碼中, 用於 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 各種值的對等 _ITERATOR_DEBUG_LEVEL 宏值。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (發行模式預設)|0 (已停用)|0 (已停用)|
|1|1 (已啟用)|0 (已停用)|
|2 (偵錯模式預設)|(不相關)|1 (在偵錯模式下啟用)|

如需了解如何停用已檢查迭代器的相關警告，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

### <a name="example"></a>範例

若要指定 _ITERATOR_DEBUG_LEVEL 宏的值, 請使用[/d](../build/reference/d-preprocessor-definitions.md)編譯器選項在命令列上定義它, 或在原始程式`#define`檔中C++包含標準程式庫標頭之前使用。 例如, 在命令列上, 若要在「偵錯工具」模式中編譯*範例 .cpp* , 並使用「偵錯工具反覆運算器」支援, 您可以指定 _ITERATOR_DEBUG_LEVEL 巨集定義:

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

在原始程式檔中，於任何定義迭代器的標準程式庫標頭之前，指定巨集。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>另請參閱

[已檢查的迭代器](../standard-library/checked-iterators.md)\
[偵錯迭代器支援](../standard-library/debug-iterator-support.md)\
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)
