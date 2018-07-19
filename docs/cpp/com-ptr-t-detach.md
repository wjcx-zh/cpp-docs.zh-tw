---
title: _com_ptr_t::Detach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c07a9ce1d315c6738472850b987ccb397feda267
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941349"
---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Microsoft 專屬**  
  
 擷取和傳回封裝的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## <a name="remarks"></a>備註  
 擷取和傳回封裝的介面指標，並接著清除封裝的指標儲存體，為 NULL。 這麼做會從封裝中移除介面指標。 它可以決定是否要呼叫`Release`上傳回的介面指標。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)