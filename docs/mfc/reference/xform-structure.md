---
title: "XFORM 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: XFORM
dev_langs: C++
helpviewer_keywords: XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f6f7121b5cc93c3f8f6f34f22d16cef888bbf15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="xform-structure"></a>XFORM 結構
`XFORM`結構具有下列格式：  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct  tagXFORM {  /* xfrm */  
    FLOAT eM11;  
    FLOAT eM12;  
    FLOAT eM21;  
    FLOAT eM22;  
    FLOAT eDx;  
    FLOAT eDy;  
} XFORM;  
```  
  
## <a name="remarks"></a>備註  
 `XFORM`結構指定的分頁空間轉換到世界空間。 **EDx**和**eDy**成員分別指定水平及垂直轉譯的元件。 下表顯示其他成員使用方式，視作業而定：  
  
|運算|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|旋轉角度的餘弦函數|旋轉角度的正弦函數|負數的旋轉角度的正弦函數|旋轉角度的餘弦函數|  
|**縮放比例**|水平縮放的元件|Nothing|Nothing|垂直縮放的元件|  
|**傾斜**|Nothing|水平的比例常數|垂直的比例常數|Nothing|  
|**反映**|水平反映元件|Nothing|Nothing|垂直反映元件|  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

