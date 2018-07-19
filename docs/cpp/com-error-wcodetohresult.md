---
title: _com_error::WCodeToHRESULT |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCodeToHRESULT
dev_langs:
- C++
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dce98775007360e3fdd4177141f7a550548d3679
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939191"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT
**Microsoft 專屬**  
  
 將對應的 16 位元*wCode*成 32 位元 HRESULT。  
  
## <a name="syntax"></a>語法  
  
```  
  
      static HRESULT WCodeToHRESULT(  
   WORD wCode   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *WCode*  
 16 位元*wCode*對應至 32 位元 HRESULT。  
  
## <a name="return-value"></a>傳回值  
 從 16 位元對應的 32 位元 HRESULT *wCode*。  
  
## <a name="remarks"></a>備註  
 請參閱[WCode](../cpp/com-error-wcode.md)成員函式。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error 類別](../cpp/com-error-class.md)