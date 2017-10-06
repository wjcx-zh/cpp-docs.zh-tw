---
title: "_com_ptr_t::Detach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
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
ms.openlocfilehash: f61b0fb05f182ef2723fdcc564fd697f490aed20
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comptrtdetach"></a>_com_ptr_t::Detach
**Microsoft 特定的**  
  
 擷取和傳回封裝的介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## <a name="remarks"></a>備註  
 擷取和傳回封裝的介面指標，然後清除 將封裝的指標儲存空間**NULL**。 這麼做會從封裝中移除介面指標。 您呼叫**發行**上傳回的介面指標。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
