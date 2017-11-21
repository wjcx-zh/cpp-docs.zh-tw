---
title: "_com_ptr_t::AddRef |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::AddRef
dev_langs: C++
helpviewer_keywords: AddRef method [C++], interface pointers
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e1230ac8bcf210e519420e8fb4ef84e77bcd4869
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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