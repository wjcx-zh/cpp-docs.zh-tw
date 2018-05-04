---
title: _com_error::Description |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7df1fb3a8ca600b888e5d6f2c51fc44fda17dd27
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)