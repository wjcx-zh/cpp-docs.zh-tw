---
title: _com_ptr_t::Release |Microsoft 文件
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
ms.openlocfilehash: 9bf83b3f6ece4e8422f1ba8dbc5d1448da6bf0c7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409640"
---
# <a name="comptrtrelease"></a>_com_ptr_t::Release
**Microsoft 特定的**  
  
 呼叫**發行**成員函式**IUnknown**封裝的介面指標上。  
  
## <a name="syntax"></a>語法  
  
```  
  
void Release( );  
  
```  
  
## <a name="remarks"></a>備註  
 呼叫`IUnknown::Release`針對封裝的介面指標，引發`E_POINTER`錯誤，如果此介面的指標是**NULL**。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)