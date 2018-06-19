---
title: _com_error::WCodeToHRESULT |Microsoft 文件
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
ms.openlocfilehash: 31b9df8305d0eea772979904f63847f6d6c2325a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413371"
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error 類別](../cpp/com-error-class.md)