---
title: _com_error::Error |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Error
- Error
dev_langs:
- C++
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a7ddaefcf3bd46bf40b03c03d2d1fb00cf8fbbb
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408423"
---
# <a name="comerrorerror"></a>_com_error::Error
**Microsoft 專屬**  
  
 擷取傳遞給建構函式的 HRESULT。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Error( ) const throw( );  
```  
  
## <a name="return-value"></a>傳回值  
 原始 HRESULT 的項目傳遞至建構函式。  
  
## <a name="remarks"></a>備註  
 擷取封裝中的 HRESULT 項目`_com_error`物件。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)