---
title: "_com_error:: wcode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::WCode
dev_langs: C++
helpviewer_keywords: WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3c26d02b6c010d17978dd517576cd74d5dd8adef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Microsoft 特定的**  
  
 擷取對應至封裝的 `HRESULT` 的 16 位元錯誤碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 如果`HRESULT`0x80040200 到 0x8004FFFF 的範圍內**WCode**方法會傳回`HRESULT`減 0x80040200; 否則它會傳回零。  
  
## <a name="remarks"></a>備註  
 **WCode**方法用於復原 COM 支援程式碼中發生的對應。 包裝函式**dispinterface**屬性或方法呼叫封裝引數並呼叫的支援常式**idispatch:: Invoke**。 傳回時，如果失敗`HRESULT`的`DISP_E_EXCEPTION`會傳回錯誤資訊會從**IDISPATCH**結構傳遞至**idispatch:: Invoke**。 錯誤碼可為儲存在 16 位元值`wCode`隸屬**IDISPATCH**結構或完整的 32 位元值**scode**隸屬**IDISPATCH**結構。 如果傳回 16 位元 `wCode`，必須先對應至 32 位元失敗 `HRESULT`。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error 類別](../cpp/com-error-class.md)