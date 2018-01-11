---
title: "_com_error::HelpContext |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::HelpContext
dev_langs: C++
helpviewer_keywords: HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2dbdd52b311a35d390a61a0601a63c1b680f79b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [_com_error 類別](../cpp/com-error-class.md)