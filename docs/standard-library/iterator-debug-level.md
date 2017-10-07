---
title: _ITERATOR_DEBUG_LEVEL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
dev_langs:
- C++
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 7a49aec5bc9a16900264ce6a5523d458299c2e86
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL
`_ITERATOR_DEBUG_LEVEL` 巨集可控制是否啟用[已檢查的迭代器](../standard-library/checked-iterators.md)和[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。 此巨集取代及結合了舊版 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 巨集的功能。  
  
## <a name="macro-values"></a>巨集值  
下表摘要說明 `_ITERATOR_DEBUG_LEVEL` 巨集的可能值。  
  
|編譯模式|巨集值|描述|  
|----------------------|----------------|-----------------|  
|**偵錯**|||  
||0|停用已檢查的迭代器及停用迭代器偵錯功能。|  
||1|啟用已檢查的迭代器，但停用迭代器偵錯功能。|  
||2 (預設)|停用迭代器偵錯功能；與已檢查的迭代器無關。|  
|**發行**|||  
||0 (預設)|停用已檢查的迭代器。|  
||1|啟用已檢查的迭代器；與迭代器偵錯功能無關。|  
  
在發行模式下，如果您將 `_ITERATOR_DEBUG_LEVEL` 指定為 2，編譯器會產生錯誤。  
  
## <a name="remarks"></a>備註  
`_ITERATOR_DEBUG_LEVEL` 巨集可控制是否啟用[已檢查的迭代器](../standard-library/checked-iterators.md)，而在「偵錯」模式下，則可控制是否啟用[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。 如果將 `_ITERATOR_DEBUG_LEVEL` 定義為 1 或 2，已檢查的迭代器便可確保您容器的界限不會被覆寫。 如果 `_ITERATOR_DEBUG_LEVEL` 是 0，則不會檢查迭代器。 當 `_ITERATOR_DEBUG_LEVEL` 定義為 1 時，任何不安全的迭代器使用方式都會導致執行階段錯誤，而使程式終止。 當 `_ITERATOR_DEBUG_LEVEL` 定義為 2 時，不安全的迭代器使用方式會導致顯示判斷提示和執行階段錯誤對話方塊，讓您可以中斷偵錯工具。 

由於 `_ITERATOR_DEBUG_LEVEL` 巨集支援的功能與 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 巨集類似，因此您可能會不確定在特定情況下要使用哪個巨集和巨集值。 為了避免混淆，建議您只使用 `_ITERATOR_DEBUG_LEVEL` 巨集。 下表說明在現有的程式碼中，針對 `_SECURE_SCL` 和 `_HAS_ITERATOR_DEBUGGING` 的各種值，要使用的對等 `_ITERATOR_DEBUG_LEVEL` 巨集值。  
  
|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (發行模式預設)|0 (已停用)|0 (已停用)|
|1|1 (已啟用)|0 (已停用)|
|2 (偵錯模式預設)|(不相關)|1 (在偵錯模式下啟用)|
  
如需了解如何停用已檢查迭代器的相關警告，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
### <a name="example"></a>範例  
  
若要指定 `_ITERATOR_DEBUG_LEVEL` 巨集的值，請在命令列上使用 [/D](../build/reference/d-preprocessor-definitions.md) 編譯器選項來定義它，或在您原始程式檔所含的「C++ 標準程式庫」標頭之前使用 `#define`。 例如，在命令列上，若要以偵錯模式編譯 *sample.cpp* 並使用偵錯迭代器支援，您可以指定 `_ITERATOR_DEBUG_LEVEL` 巨集定義：  
  
`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`  
  
在原始程式檔中，於任何定義迭代器的標準程式庫標頭之前，指定巨集。  
  
```cpp  
// sample.cpp  
  
#define _ITERATOR_DEBUG_LEVEL 1  
  
#include <vector>  
  
// ...
```  
  
## <a name="see-also"></a>另請參閱  
[已檢查的迭代器](../standard-library/checked-iterators.md)   
[偵錯迭代器支援](../standard-library/debug-iterator-support.md)   
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)

