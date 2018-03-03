---
title: "RGNDATA 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RGNDATA
dev_langs:
- C++
helpviewer_keywords:
- RGNDATA structure [MFC]
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4170b3590cc841f3edc10d4767045a4fede9782
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="rgndata-structure"></a>RGNDATA 結構
`RGNDATA` 結構包含標頭和組成區域的矩形陣列。 這些由上而下由左至右排序的矩形不會重疊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _RGNDATA { /* rgnd */  
    RGNDATAHEADER rdh;  
    char Buffer[1];  
} RGNDATA;  
```  
  
#### <a name="parameters"></a>參數  
 *rdh*  
 指定[RGNDATAHEADER](http://msdn.microsoft.com/library/windows/desktop/dd162941)結構。 （如需有關此結構的詳細資訊，請參閱 Windows SDK）。這個結構的成員指定區域類型 (它是否為矩形或梯形)、組成區域的矩形數量和包含矩形結構的緩衝區大小等等。  
  
 `Buffer`  
 指定包含任意大小的緩衝區[RECT](../../mfc/reference/rect-structure1.md)組成區域的結構。  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#getregiondata)

