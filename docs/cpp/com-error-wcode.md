---
title: '_com_error:: wcode |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9ad0cbfa614c132a75e25f46b34e37ec3a5fc64
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407000"
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Microsoft 專屬**  
  
 擷取 16 位元錯誤碼對應至封裝的 HRESULT。  
  
## <a name="syntax"></a>語法  
  
```  
WORD WCode ( ) const throw( );  
```  
  
## <a name="return-value"></a>傳回值  
 如果 HRESULT 是 0x80040200 到 0x8004FFFF 的範圍內`WCode`方法傳回的 HRESULT 減 0x80040200; 否則它會傳回零。  
  
## <a name="remarks"></a>備註  
 `WCode`方法用於復原 COM 支援程式碼中發生的對應。 包裝函式`dispinterface`屬性或方法呼叫封裝引數並呼叫支援常式`IDispatch::Invoke`。 傳回時，如果失敗 HRESULT 的`DISP_E_EXCEPTION`傳回，從擷取錯誤資訊`EXCEPINFO`結構傳遞給`IDispatch::Invoke`。 錯誤碼可能是儲存在 16 位元值`wCode`隸屬`EXCEPINFO`結構或完整的 32 位元值`scode`的成員`EXCEPINFO`結構。 如果是 16 位元`wCode`傳回時，必須先將它對應至 32 位元失敗 HRESULT。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error 類別](../cpp/com-error-class.md)