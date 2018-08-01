---
title: _com_ptr_t::Release |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t.Release
- _com_ptr_t::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method [C++]
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c5da56c3c85c17bcd2cd91f9fa5a5f8399e9528
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404271"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Microsoft 專屬**  
  
 呼叫**Release**成員函式`IUnknown`上封裝的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
void Release( );  
```  
  
## <a name="remarks"></a>備註  
 呼叫`IUnknown::Release`封裝的介面指標，引發`E_POINTER`錯誤，如果此介面的指標為 NULL。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)