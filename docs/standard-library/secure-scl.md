---
title: _SECURE_SCL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SECURE_SCL
dev_langs:
- C++
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 191cdecc193466982bc0808d517b7ad4d53c4b8d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="securescl"></a>_SECURE_SCL
  
已由 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 所取代，這個巨集會定義是否要啟用[已檢查的迭代器](../standard-library/checked-iterators.md)。 預設會在偵錯組建中啟用已檢查的迭代器，並在零售組建中停用。  
  
> [!IMPORTANT]
> 目前已不再直接使用 `_SECURE_SCL` 巨集。 請改用 `_ITERATOR_DEBUG_LEVEL` 來控制已檢查的迭代器設定。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## <a name="remarks"></a>備註  
  
若啟用了已檢查的迭代器，則使用不安全的迭代器會造成執行階段錯誤，並終止程式。 若要啟用已檢查的迭代器，將 `_ITERATOR_DEBUG_LEVEL` 設為 1 或 2。 這等同於將 `_SECURE_SCL` 設為 1 或 enabled：  
  
```  
#define _ITERATOR_DEBUG_LEVEL 1  
```  
  
若要停用已檢查的迭代器，將 `_ITERATOR_DEBUG_LEVEL` 設為 0。 這等同於將 `_SECURE_SCL` 設為 0 或 disabled：  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
如需如何停用關於已檢查迭代器之警告的相關資訊，請參閱 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
## <a name="see-also"></a>另請參閱  
[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
[已檢查的迭代器](../standard-library/checked-iterators.md)   
[偵錯迭代器支援](../standard-library/debug-iterator-support.md)   
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)


