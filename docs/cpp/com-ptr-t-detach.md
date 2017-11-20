---
title: "_com_ptr_t::Detach |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t::Detach
dev_langs: C++
helpviewer_keywords: Detach method [C++]
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ddb1d52ab9706293a03be074c3698c35c1bf291c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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