---
title: "XFORM 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- XFORM
dev_langs:
- C++
helpviewer_keywords:
- XFORM structure
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
caps.latest.revision: 11
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2d23b3838f1e2dcabb2affb96fa6f18942581ff8
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="xform-structure"></a>XFORM 結構
`XFORM`結構具有下列格式︰  
  
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
 `XFORM`結構指定分頁空間轉換到全局空間。 **EDx**和**eDy**成員分別指定水平及垂直轉譯的元件。 下表顯示其他成員使用方式，視作業而定︰  
  
|運算|eM11|eM12|eM21|eM22|  
|---------------|----------|----------|----------|----------|  
|`Rotation`|旋轉角度的餘弦函數|旋轉角度的正弦函數|負數的旋轉角度的正弦函數|旋轉角度的餘弦函數|  
|**縮放比例**|水平縮放的元件|Nothing|Nothing|垂直縮放的元件|  
|**傾斜**|Nothing|水平的比例常數|垂直的比例常數|Nothing|  
|**反映**|水平反映元件|Nothing|Nothing|垂直反映元件|  
  
## <a name="requirements"></a>需求  
 **標頭︰** wingdi.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)


