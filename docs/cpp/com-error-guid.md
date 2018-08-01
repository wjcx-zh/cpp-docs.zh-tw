---
title: _com_error::GUID |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::GUID
dev_langs:
- C++
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c592607732eb5558ce74edb7b71adbc023b2ae52
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402279"
---
# <a name="comerrorguid"></a>_com_error::GUID
**Microsoft 專屬**  
  
 呼叫`IErrorInfo::GetGUID`函式。  
  
## <a name="syntax"></a>語法  
  
```  
GUID GUID( ) const throw( );  
```  
  
## <a name="return-value"></a>傳回值  
 傳回的結果`IErrorInfo::GetGUID`for`IErrorInfo`物件記錄`_com_error`物件。 如果沒有`IErrorInfo`記錄物件時，它會傳回`GUID_NULL`。  
  
## <a name="remarks"></a>備註  
 呼叫時的任何失敗`IErrorInfo::GetGUID`方法會被忽略。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)