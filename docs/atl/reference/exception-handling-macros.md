---
title: "例外狀況處理巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
dev_langs: C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 424a65c44d7bb22d1fef6e21e1892967ecd3e9b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exception-handling-macros"></a>例外狀況處理巨集
這些巨集提供例外狀況處理的支援。  
  
|||  
|-|-|  
|[_ATLCATCH](#_atlcatch)|陳述式來處理發生在相關聯的錯誤`_ATLTRY`。|  
|[_ATLCATCHALL](#_atlcatchall)|陳述式來處理發生在相關聯的錯誤`_ATLTRY`。|  
|[_ATLTRY](#_atltry)|標記可能發生的錯誤可能的防護程式碼區段。|  
  
## <a name="requirements"></a>需求：
**標頭：** atldef.h

##  <a name="_atlcatch"></a>_ATLCATCH  
 陳述式來處理發生在相關聯的錯誤`_ATLTRY`。  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>參數  
 *e*  
 若要攔截例外狀況。  
  
### <a name="remarks"></a>備註  
 搭配`_ATLTRY`。 解析成 c + + [catch (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md)處理針對給定的 c + + 例外狀況類型。  
  
##  <a name="_atlcatchall"></a>_ATLCATCHALL  
 陳述式來處理發生在相關聯的錯誤`_ATLTRY`。  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>備註  
 搭配`_ATLTRY`。 解析成 c + + [catch](../../cpp/try-throw-and-catch-statements-cpp.md)處理所有類型的 c + + 例外狀況。  
  
##  <a name="_atltry"></a>_ATLTRY  
 標記可能發生的錯誤可能的防護程式碼區段。  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>備註  
 搭配[_ATLCATCH](#_atlcatch)或[_ATLCATCHALL](#_atlcatchall)。 C + + 符號會解析[再試一次](../../cpp/try-throw-and-catch-statements-cpp.md)。  
  
## <a name="see-also"></a>請參閱  
 [巨集](../../atl/reference/atl-macros.md)
