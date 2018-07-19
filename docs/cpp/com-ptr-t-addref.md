---
title: _com_ptr_t::AddRef |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40ed48b54a3862f7ac5804e7652d98b661bb071d
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940988"
---
# <a name="comptrtaddref"></a>_com_ptr_t::AddRef
**Microsoft 專屬**  
  
 呼叫`AddRef`成員函式`IUnknown`上封裝的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
void AddRef( );  
  
```  
  
## <a name="remarks"></a>備註  
 呼叫`IUnknown::AddRef`封裝的介面指標，E_POINTER 錯誤才增加指標為 NULL。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)