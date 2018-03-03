---
title: "ABCFLOAT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b58871df5a526455297dd6d092f98e9facd901ae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="abcfloat-structure"></a>ABCFLOAT 結構
`ABCFLOAT`結構包含 A、 B 和 C 字型字元寬度。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _ABCFLOAT { /* abcf */  
    FLOAT abcfA;  
    FLOAT abcfB;  
    FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### <a name="parameters"></a>參數  
 *abcfA*  
 指定字元的 A 間距。 A 間距是在繪製字元圖像之前要加入至目前位置的距離。  
  
 *abcfB*  
 指定字元的 B 間距。 B 間距是繪製字元圖像部分的寬度。  
  
 *abcfC*  
 指定字元的 C 間距。 C 間距是要加入至目前位置，以便在字元圖像右邊加上空白字元的距離。  
  
## <a name="remarks"></a>備註  
 A、 B 和 C 寬度會測量基底線條的字型。 字元增量 （總寬度） 的字元是 A、 B 和 C 空間的總和。 A 或 C 間距可以是負數值，用於標示留白部分或突出部分。  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

