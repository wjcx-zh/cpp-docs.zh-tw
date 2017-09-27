---
title: "_com_error::HRESULTToWCode |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HRESULTToWCode
- _com_error.HRESULTToWCode
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
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
ms.openlocfilehash: 296c6f43c1bc840ae13bdf4ad355d7f41e2cc3fd
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode
**Microsoft 特定的**  
  
 32 位元會對應`HRESULT`至 16 位元`wCode`。  
  
## <a name="syntax"></a>語法  
  
```  
  
      static WORD HRESULTToWCode(  
   HRESULT hr   
) throw( );  
```  
  
#### <a name="parameters"></a>參數  
 `hr`  
 32 位元`HRESULT`對應到 16 位元`wCode`。  
  
## <a name="return-value"></a>傳回值  
 16 位元`wCode`從 32 位元對應`HRESULT`。  
  
## <a name="remarks"></a>備註  
 請參閱[_com_error:: wcode](../cpp/com-error-wcode.md)如需詳細資訊。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error:: wcode](../cpp/com-error-wcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error 類別](../cpp/com-error-class.md)
