---
title: "點結構&1; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- POINT
- LPPOINT
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure
- POINT structure
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
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
translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: d1e2bb05f9bad785b13e79413866d8e0ce1e1faa
ms.lasthandoff: 02/24/2017

---
# <a name="point-structure1"></a>點結構&1;
**點**結構會定義 x* - *和點的 y 座標。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagPOINT {  
    LONG x;  
    LONG y;  
} POINT;  
```  
  
#### <a name="parameters"></a>參數  
 *x*  
 指定點的 x 座標。  
  
 *y*  
 指定點的 y 座標。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&37;](../../mfc/codesnippet/cpp/point-structure1_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** windef.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPoint 類別](../../atl-mfc-shared/reference/cpoint-class.md)

