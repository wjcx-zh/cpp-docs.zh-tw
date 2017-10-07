---
title: "_com_error::Description |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 0d91f6fded1fa1c4ea4d44cadd0d9285913b5f42
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comerrordescription"></a>_com_error::Description
**Microsoft 特定的**  
  
 呼叫**ierrorinfo:: Getdescription**函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
_bstr_t Description( ) const;  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的結果**ierrorinfo:: Getdescription**如**IErrorInfo**物件記錄內`_com_error`物件。 產生的 `BSTR` 會封裝在 `_bstr_t` 物件內。 如果沒有**IErrorInfo**是記錄，則傳回一個空`_bstr_t`。  
  
## <a name="remarks"></a>備註  
 呼叫**ierrorinfo:: Getdescription**函式並擷取**IErrorInfo**記錄內`_com_error`物件。 呼叫時的任何失敗**ierrorinfo:: Getdescription**方法會被忽略。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)
