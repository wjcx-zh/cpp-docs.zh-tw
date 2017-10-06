---
title: "_com_error::HelpContext |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::HelpContext
dev_langs:
- C++
helpviewer_keywords:
- HelpContext method
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
caps.latest.revision: 6
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d3eb0678e7d3b7cb4c1824cf17bc25499bf0c0ce
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext
**Microsoft 特定的**  
  
 呼叫**Gethelpcontext**函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
DWORD HelpContext( ) const throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的結果**Gethelpcontext**如**IErrorInfo**物件記錄內`_com_error`物件。 如果沒有**IErrorInfo**記錄物件，它會傳回零。  
  
## <a name="remarks"></a>備註  
 呼叫時的任何失敗**Gethelpcontext**方法會被忽略。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)
