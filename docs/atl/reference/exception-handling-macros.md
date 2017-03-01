---
title: "例外狀況處理巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 9d99551d8dbe116c9f4fafeb9602e471839003a7
ms.lasthandoff: 02/24/2017

---
# <a name="exception-handling-macros"></a>例外狀況處理巨集
這些巨集提供例外狀況處理的支援。  
  
|||  
|-|-|  
|[_ATLCATCH](#_atlcatch)|處理相關聯中發生之錯誤的陳述式`_ATLTRY`。|  
|[_ATLCATCHALL](#_atlcatchall)|處理相關聯中發生之錯誤的陳述式`_ATLTRY`。|  
|[_ATLTRY](#_atltry)|標記受保護的程式碼區段，其中可能會發生錯誤。|  
  
##  <a name="a-nameatlcatcha--atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH  
 處理相關聯中發生之錯誤的陳述式`_ATLTRY`。  
  
```
_ATLCATCH(e)
```  
  
### <a name="parameters"></a>參數  
 *e*  
 若要攔截例外狀況。  
  
### <a name="remarks"></a>備註  
 搭配`_ATLTRY`。 解析成 c + +[攔截 (CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md)處理 c + + 例外狀況的指定型別。  
  
##  <a name="a-nameatlcatchalla--atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL  
 處理相關聯中發生之錯誤的陳述式`_ATLTRY`。  
  
```
_ATLCATCHALL
```  
  
### <a name="remarks"></a>備註  
 搭配`_ATLTRY`。 解析成 c + + [catch](../../cpp/try-throw-and-catch-statements-cpp.md)處理所有類型的 c + + 例外狀況。  
  
##  <a name="a-nameatltrya--atltry"></a><a name="_atltry"></a>_ATLTRY  
 標記受保護的程式碼區段，其中可能會發生錯誤。  
  
```
_ATLTRY
```  
  
### <a name="remarks"></a>備註  
 搭配[_ATLCATCH](#_atlcatch)或[_ATLCATCHALL](#_atlcatchall)。 C + + 符號解析[嘗試](../../cpp/try-throw-and-catch-statements-cpp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

