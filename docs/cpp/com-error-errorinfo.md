---
title: _com_error::ErrorInfo |Microsoft 文件
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
ms.openlocfilehash: 8fbc735dfae1b30209eccfd14f1170826fb07680
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410989"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo
**Microsoft 特定的**  
  
 擷取**IErrorInfo**物件傳遞至建構函式。  
  
## <a name="syntax"></a>語法  
  
```  
  
IErrorInfo * ErrorInfo( ) const throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 原始**IErrorInfo**項目傳遞至建構函式。  
  
## <a name="remarks"></a>備註  
 擷取封裝**IErrorInfo**中的項目`_com_error`物件，或**NULL**有**IErrorInfo**項目記錄。 呼叫端必須呼叫**發行**上傳回的物件完成時使用它。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)