---
title: "_com_ptr_t::AddRef |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: d873d91192dc13f7b1277cbe8ef26b24421b6904
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Microsoft 特定的**  
  
 呼叫`AddRef`成員函式**IUnknown**封裝的介面指標上。  
  
## <a name="syntax"></a>語法  
  
```  
  
void AddRef( );  
  
```  
  
## <a name="remarks"></a>備註  
 呼叫`IUnknown::AddRef`針對封裝的介面指標，引發`E_POINTER`指標是否錯誤**NULL**。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
