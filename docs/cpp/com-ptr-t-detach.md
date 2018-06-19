---
title: _com_ptr_t::Detach |Microsoft 文件
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
ms.openlocfilehash: 6fbe8fd203c3fda75e83aee623254676dacaf1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410576"
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
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)