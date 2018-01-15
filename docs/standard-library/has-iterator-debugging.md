---
title: _HAS_ITERATOR_DEBUGGING | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _HAS_ITERATOR_DEBUGGING
dev_langs: C++
helpviewer_keywords: _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c680338fa84fa0f00e01ea4612d07c851570a36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING  
  
此巨集 (已被 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 取代) 定義偵錯組建中是否啟用迭代器偵錯功能。 預設會在「偵錯」組建中啟用迭代器偵錯功能，而在「零售」組建中停用此功能。 如需詳細資訊，請參閱[偵錯迭代器支援](../standard-library/debug-iterator-support.md)。  
  
> [!IMPORTANT]
> 目前已不再直接使用 `_HAS_ITERATOR_DEBUGGING` 巨集。 請改用 `_ITERATOR_DEBUG_LEVEL` 來控制迭代器偵錯設定。 如需詳細資訊，請參閱 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## <a name="remarks"></a>備註  
若要在偵錯組建中啟用迭代器偵錯功能，請將 `_ITERATOR_DEBUG_LEVEL` 設定為 2。 這等同於將 `_HAS_ITERATOR_DEBUGGING` 設定為 1 或 enabled：  
  
```  
#define _ITERATOR_DEBUG_LEVEL 2  
```  
  
在偵錯組建中，`_ITERATOR_DEBUG_LEVEL` 不能設定為 2 (且 `_HAS_ITERATOR_DEBUGGING` 不能設定為 1)。  
  
若要在偵錯組建中停用偵錯迭代器，請將 `_ITERATOR_DEBUG_LEVEL` 設定為 0 或 1。 這等同於將 `_HAS_ITERATOR_DEBUGGING` 設定為 0 或 disabled：  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
## <a name="see-also"></a>請參閱  
 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
 [偵錯迭代器支援](../standard-library/debug-iterator-support.md)   
 [已檢查的迭代器](../standard-library/checked-iterators.md)   
 [安全程式庫：C++ 標準程式庫](../standard-library/safe-libraries-cpp-standard-library.md)

