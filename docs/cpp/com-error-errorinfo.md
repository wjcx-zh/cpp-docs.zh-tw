---
title: _com_error::ErrorInfo |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3f4d105efb7269c0c1344d6a9399ebbe4fa9fd2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404290"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Microsoft 專屬**  
  
 擷取`IErrorInfo`物件傳遞至建構函式。  
  
## <a name="syntax"></a>語法  
  
```  
IErrorInfo * ErrorInfo( ) const throw( );  
```  
  
## <a name="return-value"></a>傳回值  
 傳入建構函式的原始 `IErrorInfo` 項目。  
  
## <a name="remarks"></a>備註  
 擷取封裝`IErrorInfo`中的項目`_com_error`物件，或如果沒有則為 NULL`IErrorInfo`項目記錄。 呼叫端必須呼叫`Release`上傳回的物件完成時使用它。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)