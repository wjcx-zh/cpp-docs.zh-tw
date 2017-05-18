---
title: "_pAtlModule |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
- _pAtlModule
- ATL::_pAtlModule
- ATL._pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- pAtlModule variable
- _pAtlModule variable
ms.assetid: 0ecde3a9-3f4d-4c7b-bb54-713ce05c4777
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: b20c5010616323eac9438223df64af9960192e2b
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="patlmodule"></a>_pAtlModule
儲存目前的模組指標的全域變數。  
  
## <a name="syntax"></a>語法  
  
```  
__declspec(selectany) CAtlModule* _pAtlModule  
```  
  
## <a name="remarks"></a>備註  
 針對這個全域變數的方法可以用來提供的功能，（現在已過時） 類別[CComModule](../../atl/reference/ccommodule-class.md)提供在 Visual c + + 6.0。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&97;](../../atl/codesnippet/cpp/patlmodule_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  
  
## <a name="see-also"></a>另請參閱  
 [全域變數](../../atl/reference/atl-global-variables.md)




