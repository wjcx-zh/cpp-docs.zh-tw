---
title: "_com_error::_com_error |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::_com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df04357afd35b546fb43c90a102b7dc0cacdc95e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorcomerror"></a>_com_error::_com_error
**Microsoft 特定的**  
  
 建構 `_com_error` 物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
      _com_error(  
   HRESULT hr,  
   IErrorInfo* perrinfo = NULL,  
   bool fAddRef=false  
) throw( );  
_com_error(  
   const _com_error& that   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `hr`  
 `HRESULT` 資訊。  
  
 `perrinfo`  
 **IErrorInfo**物件。  
  
 **bool fAddRef = false**  
 導致建構函式，以在非 null 值上呼叫 AddRef **IErrorInfo**介面。 如此可在將介面的擁有權傳入 `_com_error` 物件的一般情況下，提供正確的參考計數，例如：  
  
```  
throw _com_error(hr, perrinfo);  
```  
  
 如果您不想要傳送擁有權，以您的程式碼`_com_error`物件，而`AddRef`才能位移**發行**中`_com_error`解構函式建構物件，如下所示：  
  
```  
_com_error err(hr, perrinfo, true);  
```  
  
 `that`  
 現有的 `_com_error` 物件。  
  
## <a name="remarks"></a>備註  
 第一個建構函式會建立新的物件，指定`HRESULT`和選擇性**IErrorInfo**物件。 第二個方法會建立現有 `_com_error` 物件的複本。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_com_error 類別](../cpp/com-error-class.md)