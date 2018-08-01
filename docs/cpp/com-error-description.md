---
title: _com_error::Description |Microsoft Docs
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
ms.openlocfilehash: 848709fa6cbbbfb4166750f86540de2433a73023
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404024"
---
# <a name="comerrordescription"></a>_com_error::Description
**Microsoft 專屬**  
  
 呼叫`IErrorInfo::GetDescription`函式。  
  
## <a name="syntax"></a>語法  
  
```  
_bstr_t Description( ) const;  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的結果`IErrorInfo::GetDescription`for`IErrorInfo`物件記錄`_com_error`物件。 產生的 `BSTR` 會封裝在 `_bstr_t` 物件內。 如果沒有`IErrorInfo`是記錄，它會傳回空`_bstr_t`。  
  
## <a name="remarks"></a>備註  
 呼叫`IErrorInfo::GetDescription`函式並擷取`IErrorInfo`記錄`_com_error`物件。 呼叫時的任何失敗`IErrorInfo::GetDescription`方法會被忽略。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)