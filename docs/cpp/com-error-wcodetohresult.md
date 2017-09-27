---
title: "_com_error::WCodeToHRESULT |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
- _com_error.WCodeToHRESULT
- WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: e5165f3bf0058d2c1f5ae4cb416fd6b26e0077d3
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Microsoft 特定的**  
  
 將 16 位元的 `wCode` 對應至 32 位元的 `HRESULT`。  
  
## <a name="syntax"></a>語法  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `wCode`  
 要對應到 32 位元 `wCode` 的 16 位元 `HRESULT`。  
  
## <a name="return-value"></a>傳回值  
 從 16 位元 `HRESULT` 對應過來的 32 位元 `wCode`。  
  
## <a name="remarks"></a>備註  
 請參閱[WCode](../cpp/com-error-wcode.md)成員函式。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error 類別](../cpp/com-error-class.md)
