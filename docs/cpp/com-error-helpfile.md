---
title: _com_error::HelpFile |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HelpFile
dev_langs:
- C++
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1f02238d228b5de4302812bacf4f9ad5cf1300c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409783"
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)