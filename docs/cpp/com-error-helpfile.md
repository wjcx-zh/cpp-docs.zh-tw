---
title: "_com_error::HelpFile |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
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
ms.openlocfilehash: 7e1e9ec8c7d6684bb7b244fd9ba6773b6f1460e1
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile
**Microsoft 特定的**  
  
 呼叫**ierrorinfo:: Gethelpfile**函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
_bstr_t HelpFile() const;  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的結果**ierrorinfo:: Gethelpfile**如**IErrorInfo**物件記錄內`_com_error`物件。 產生的 BSTR 會封裝在 `_bstr_t` 物件內。 如果沒有**IErrorInfo**是記錄，則傳回一個空`_bstr_t`。  
  
## <a name="remarks"></a>備註  
 呼叫時的任何失敗**ierrorinfo:: Gethelpfile**方法會被忽略。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)
