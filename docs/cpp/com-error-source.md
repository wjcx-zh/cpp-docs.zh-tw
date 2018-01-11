---
title: "_com_error::Source |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::Source
dev_langs: C++
helpviewer_keywords: Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a725ddb3ff72acc749a5dbf09d2ddcc94856590c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorsource"></a>_com_error::Source
**Microsoft 特定的**  
  
 呼叫**Getsource**函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
_bstr_t Source() const;  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的結果**Getsource**如**IErrorInfo**物件記錄內`_com_error`物件。 產生的 BSTR 會封裝在 `_bstr_t` 物件內。 如果沒有**IErrorInfo**是記錄，則傳回一個空`_bstr_t`。  
  
## <a name="remarks"></a>備註  
 呼叫時的任何失敗**Getsource**方法會被忽略。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_com_error 類別](../cpp/com-error-class.md)