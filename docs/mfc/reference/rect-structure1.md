---
title: "RECT 結構&1; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure
- LPRECT structure
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
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
ms.openlocfilehash: bc91b22f291f23ed396a054b0c929410718286a3
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="rect-structure1"></a>RECT 結構&1;
`RECT` 結構定義矩形的左上角和右下角的座標。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagRECT {  
    LONG left;  
    LONG top;  
    LONG right;  
    LONG bottom;  
} RECT;  
```  
  
## <a name="members"></a>Members  
 `left`  
 指定矩形左上角的 x 座標。  
  
 `top`  
 指定矩形左上角的 y 座標。  
  
 `right`  
 指定矩形右下角的 x 座標。  
  
 `bottom`  
 指定矩形右下角的 y 座標。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&38;](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** windef.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect 類別](../../atl-mfc-shared/reference/crect-class.md)

