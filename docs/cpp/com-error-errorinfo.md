---
title: "_com_error::ErrorInfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::ErrorInfo
dev_langs: C++
helpviewer_keywords: ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 642078d84f72a553e9b2407b279265a3a7e77522
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [_com_error 類別](../cpp/com-error-class.md)