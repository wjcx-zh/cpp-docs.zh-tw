---
title: _com_error::HRESULTToWCode |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbcbd73f1a4a6d80ed30a5d70ca43d5fe45677f9
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941713"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Microsoft 專屬**  
  
 對應到 16 位元的 32 位元 HRESULT `wCode`。  
  
## <a name="syntax"></a>語法  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *hr*  
 對應到 16 位元的 32 位元 HRESULT `wCode`。  
  
## <a name="return-value"></a>傳回值  
 16 位元`wCode`從 32 位元 HRESULT 對應。  
  
## <a name="remarks"></a>備註  
 請參閱[_com_error:: wcode](../cpp/com-error-wcode.md)如需詳細資訊。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error 類別](../cpp/com-error-class.md)