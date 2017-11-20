---
title: "_com_error::GUID |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::GUID
dev_langs: C++
helpviewer_keywords: GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6c15c3890e5d5aa6e20cd0898f30aa0f56f50cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorguid"></a>_com_error::GUID
**Microsoft 特定的**  
  
 呼叫**Getguid**函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
GUID GUID( ) const throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的結果**Getguid**如**IErrorInfo**物件記錄內`_com_error`物件。 如果沒有**IErrorInfo**記錄物件時，它會傳回`GUID_NULL`。  
  
## <a name="remarks"></a>備註  
 呼叫時的任何失敗**Getguid**方法會被忽略。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)