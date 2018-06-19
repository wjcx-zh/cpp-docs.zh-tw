---
title: RECT 結構 1 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b61c794b8fa383eeea62459a5a83948ef2efe10
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372589"
---
# <a name="rect-structure1"></a>RECT 結構 1
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
  
## <a name="members"></a>成員  
 `left`  
 指定矩形左上角的 x 座標。  
  
 `top`  
 指定矩形左上角的 y 座標。  
  
 `right`  
 指定矩形右下角的 x 座標。  
  
 `bottom`  
 指定矩形右下角的 y 座標。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** windef.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect 類別](../../atl-mfc-shared/reference/crect-class.md)
