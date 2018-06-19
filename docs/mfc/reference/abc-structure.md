---
title: ABC 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61b5f67247b556b37cdf934f94c30947675533e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346486"
---
# <a name="abc-structure"></a>ABC 結構
**ABC**結構包含 TrueType 字型中的字元寬度。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _ABC { /* abc */  
    int abcA;  
    UINT abcB;  
    int abcC;  
} ABC;  
```  
  
#### <a name="parameters"></a>參數  
 *abcA*  
 指定字元的 A 間距。 A 間距是在繪製字元圖像之前要加入至目前位置的距離。  
  
 *abcB*  
 指定字元的 B 間距。 B 間距是繪製字元圖像部分的寬度。  
  
 *abcC*  
 指定字元的 C 間距。 C 間距是要加入至目前位置，以便在字元圖像右邊加上空白字元的距離。  
  
## <a name="remarks"></a>備註  
 字元的總寬度為 A、B 和 C 間距的總和。 A 或 C 間距可以是負數值，用於標示留白部分或突出部分。  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


