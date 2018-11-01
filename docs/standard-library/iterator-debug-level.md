---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: a584fe5a97e251205e750507b27e53e6e7b9a20e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502813"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

_ITERATOR_DEBUG_LEVEL 巨集可控制是否[檢查的迭代器](../standard-library/checked-iterators.md)並[偵錯迭代器支援](../standard-library/debug-iterator-support.md)已啟用。 這個巨集取代，並結合了較舊的 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 巨集的功能。

## <a name="macro-values"></a>巨集值

下表摘要說明您 _ITERATOR_DEBUG_LEVEL 巨集的可能值。

|編譯模式|巨集值|描述|
|----------------------|----------------|-----------------|
|**偵錯**|||
||0|停用已檢查的迭代器及停用迭代器偵錯功能。|
||1|啟用已檢查的迭代器，但停用迭代器偵錯功能。|
||2 (預設)|停用迭代器偵錯功能；與已檢查的迭代器無關。|
|**發行**|||
||0 (預設)|停用已檢查的迭代器。|
||1|啟用已檢查的迭代器；與迭代器偵錯功能無關。|

在發行模式中，編譯器會產生錯誤，如果您指定 _ITERATOR_DEBUG_LEVEL 為 2。

## <a name="remarks"></a>備註

_ITERATOR_DEBUG_LEVEL 巨集可控制是否[檢查的迭代器](../standard-library/checked-iterators.md)已啟用，以及在偵錯模式、 是否[偵錯迭代器支援](../standard-library/debug-iterator-support.md)已啟用。 如果 _ITERATOR_DEBUG_LEVEL 定義為 1 或 2，已檢查的迭代器會確保您容器的界限不會覆寫。 如果 _ITERATOR_DEBUG_LEVEL 為 0，不會檢查的迭代器。 當 _ITERATOR_DEBUG_LEVEL 定義為 1 時，任何不安全的迭代器使用會造成執行階段錯誤，則會終止程式。 當 _ITERATOR_DEBUG_LEVEL 定義為 2 時，不安全的迭代器會使用顯示判斷提示和執行階段錯誤對話方塊，可讓您中斷偵錯工具的原因。

因為 _ITERATOR_DEBUG_LEVEL 巨集支援 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 巨集類似的功能，您可能會不確定哪個巨集和巨集要在特定情況下使用的值。 為了避免混淆，我們建議您使用 _ITERATOR_DEBUG_LEVEL 巨集。 下表描述要用於 _SECURE_SCL 和 _HAS_ITERATOR_DEBUGGING 現有程式碼中的各種值的對等的 _ITERATOR_DEBUG_LEVEL 巨集值。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (發行模式預設)|0 (已停用)|0 (已停用)|
|1|1 (已啟用)|0 (已停用)|
|2 (偵錯模式預設)|(不相關)|1 (在偵錯模式下啟用)|

如需了解如何停用已檢查迭代器的相關警告，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。

### <a name="example"></a>範例

若要指定 _ITERATOR_DEBUG_LEVEL 巨集的值，請使用[/D](../build/reference/d-preprocessor-definitions.md)編譯器選項，來定義命令列上，或使用`#define`之前 c + + 標準程式庫標頭會包含在原始程式檔。 比方說，在命令列上，若要編譯*sample.cpp*偵錯模式中，並使用偵錯迭代器支援，您可以指定 _ITERATOR_DEBUG_LEVEL 巨集定義：

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

在原始程式檔中，於任何定義迭代器的標準程式庫標頭之前，指定巨集。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>另請參閱

[Checked Iterators](../standard-library/checked-iterators.md)<br/>
[Debug Iterator Support](../standard-library/debug-iterator-support.md)<br/>
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
