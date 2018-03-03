---
title: "LOGPEN 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b7bfa598a59f62c11dbda13356559816b5bd47ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="logpen-structure"></a>LOGPEN 結構
`LOGPEN`結構會定義樣式、 寬度和色彩的畫筆、 繪圖物件，用來繪製線條和框線。 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)函式使用`LOGPEN`結構。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagLOGPEN {  /* lgpn */  
    UINT lopnStyle;  
    POINT lopnWidth;  
    COLORREF lopnColor;  
} LOGPEN;  
```  
  
#### <a name="parameters"></a>參數  
 *lopnStyle*  
 指定的畫筆類型。 這個成員可以是下列值之一：  
  
- **PS_SOLID**建立實心筆。  
  
- **PS_DASH**建立虛線的畫筆。 （時才有效畫筆寬度為 1。）  
  
- **PS_DOT**建立虛線的畫筆。 （時才有效畫筆寬度為 1。）  
  
- **PS_DASHDOT**建立畫筆交替的虛線和點。 （時才有效畫筆寬度為 1。）  
  
- **PS_DASHDOTDOT**建立畫筆交替的虛線和雙句點。 （時才有效畫筆寬度為 1。）  
  
- **PS_NULL**建立 null 畫筆。  
  
- **PS_INSIDEFRAME**建立畫筆繪製線條，以指定的周框的 GDI 輸出函式所產生的封閉圖形的框架內，(比方說，**橢圓形**，**矩形**， `RoundRect`， `Pie`，和`Chord`成員函式)。 當此樣式會搭配 GDI 輸出未指定的周框的函式 (例如，`LineTo`成員函式)，畫筆的繪圖區域不會限制在範圍內。  
  
     如果畫筆有**PS_INSIDEFRAME**樣式和色彩的不符合在邏輯的色彩，色彩畫筆會繪製遞色色彩。 **PS_SOLID**畫筆樣式不能用來建立畫筆，與遞色色彩。 **PS_INSIDEFRAME**樣式等同於**PS_SOLID**畫筆寬度小於或等於 1 時。  
  
     當**PS_INSIDEFRAME**樣式會搭配所產生的函式以外的 GDI 物件**橢圓形**，**矩形**，和`RoundRect`，線條可能不完整指定的範圍內。  
  
 *lopnWidth*  
 指定的畫筆寬度，以邏輯單位表示。 如果**lopnWidth**成員為 0，畫筆為 1 個像素寬點陣不論目前的對應模式的裝置上。  
  
 *lopnColor*  
 指定的畫筆色彩。  
  
## <a name="remarks"></a>備註  
 **y**值[點](../../mfc/reference/point-structure1.md)結構**lopnWidth**成員不是。  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

