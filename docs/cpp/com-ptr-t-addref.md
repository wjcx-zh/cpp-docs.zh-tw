---
title: _com_ptr_t::AddRef |Microsoft 文件
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
ms.openlocfilehash: 54a1b629f254bae2b72790546bcbb00185f2c44c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409770"
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)