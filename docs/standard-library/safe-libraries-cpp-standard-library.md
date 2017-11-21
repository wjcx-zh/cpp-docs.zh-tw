---
title: "安全程式庫：C++ 標準程式庫 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _SCL_SECURE_NO_DEPRECATE
dev_langs: C++
helpviewer_keywords:
- Safe Libraries
- Safe Libraries, C++ Standard Library
- Safe C++ Standard Library
ms.assetid: 3993340f-1f29-4d81-b3f5-52a52bc8e148
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8cc4b94534845901a900a8c0ecff1d89c6bb600
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="safe-libraries-c-standard-library"></a>安全程式庫：C++ 標準程式庫
Visual C++ 隨附的程式庫 (包括 C++ 標準程式庫) 已做了數項改進，因此更安全。  
  
 C++ 標準程式庫中有幾個方法已知可能不安全，因為這些方法可能導致緩衝區溢位或其他程式碼缺失。 建議您不要使用這些方法，目前已建立更安全的新方法來取代這些方法。 這些新方法的結尾全部都是 `_s`。  
  
 迭代器和演算法也已做了數項改進，因此更安全。 如需詳細資訊，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)、[偵錯迭代器支援](../standard-library/debug-iterator-support.md)和 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## <a name="remarks"></a>備註  
 下表列出可能不安全的 C++ 標準程式庫方法，以及更安全的對等項目：  
  
|可能不安全的方法|更安全的對等項目|  
|-------------------------------|----------------------|  
|[copy](../standard-library/basic-string-class.md#copy)|[basic_string::_Copy_s](../standard-library/basic-string-class.md#copy_s)|  
|[copy](../standard-library/char-traits-struct.md#copy)|[char_traits::_Copy_s](../standard-library/char-traits-struct.md#copy_s)|  
  
 如果您呼叫上述任何一個可能不安全的方法，或不當使用迭代器，編譯器將會產生[編譯器警告 (層級 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 如需如何停用這些警告的相關資訊，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)  
  
 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)  
  
 [Checked Iterators](../standard-library/checked-iterators.md)  
  
 [偵錯迭代器支援](../standard-library/debug-iterator-support.md)  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)

