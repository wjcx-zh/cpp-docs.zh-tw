---
title: _SECURE_SCL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _SECURE_SCL
dev_langs: C++
helpviewer_keywords: _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f32a4ebfd9aec0cfbdcc03098f6aa0a23b8ecff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
[已檢查的迭代器](../standard-library/checked-iterators.md)   
[偵錯迭代器支援](../standard-library/debug-iterator-support.md)   
[安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)

