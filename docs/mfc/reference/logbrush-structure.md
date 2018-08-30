---
title: LOGBRUSH 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b868efed07f786a78c516862e1f88d2310a7c05d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208774"
---
# <a name="logbrush-structure"></a>LOGBRUSH 結構
`LOGBRUSH`結構會定義樣式、 色彩和實體的筆刷的模式。 它由 Windows [CreateBrushIndirect](/windows/desktop/api/wingdi/nf-wingdi-createbrushindirect)並[ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen)函式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>參數  
 *lbStyle*  
 指定的筆刷樣式。 `lbStyle`成員必須是其中一個下列樣式：  
  
- 裝置獨立點陣圖 (DIB) 規格由 BS_DIBPATTERN 的圖樣筆刷。 如果*lbStyle*是 BS_DIBPATTERN，`lbHatch`成員包含封裝的 DIB 的控制代碼。  
  
- 裝置獨立點陣圖 (DIB) 規格由 BS_DIBPATTERNPT 的圖樣筆刷。 如果*lbStyle*是 BS_DIBPATTERNPT，`lbHatch`成員包含封裝的 DIB 的指標。  
  
- BS_HATCHED 影線的筆刷。  
  
- BS_HOLLOW 空心的筆刷。  
  
- BS_NULL BS_HOLLOW 與相同。  
  
- 記憶體點陣圖所定義的筆刷 BS_PATTERN 模式。  
  
- BS_SOLID 實心筆刷。  
  
 *lbColor*  
 指定要繪製的筆刷的色彩。 如果*lbStyle*是 BS_HOLLOW 或 BS_PATTERN 樣式*lbColor*會被忽略。 如果*lbStyle* BS_DIBPATTERN 或 BS_DIBPATTERNBT 的低序位字組*lbColor*指定是否`bmiColors`的成員[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)結構包含目前具現化的邏輯色板明確紅、 綠、 藍 (RGB) 值或索引。 `lbColor`成員必須是下列值之一：  
  
- 到目前的具現化的邏輯色板的 16 位元索引陣列包含 DIB_PAL_COLORS color 資料表。  
  
- DIB_RGB_COLORS 色彩表包含常值的 RGB 值。  
  
 *lbHatch*  
 指定影線樣式。 意義取決於所定義的筆刷樣式*lbStyle*。 如果*lbStyle*是 BS_DIBPATTERN，`lbHatch`成員包含封裝的 DIB 的控制代碼。 如果*lbStyle*是 BS_DIBPATTERNPT，`lbHatch`成員包含封裝的 DIB 的指標。 如果*lbStyle*是 BS_HATCHED，`lbHatch`成員指定用來建立的規劃線條的方向。 它可以是下列值之一：  
  
- HS_BDIAGONAL 的 45 度的上、 左到右規劃  
  
- HS_CROSS 水平及垂直有斜紋  
  
- HS_DIAGCROSS 45 度有斜紋  
  
- HS_FDIAGONAL 的 45 度的向下、 左到右規劃  
  
- HS_HORIZONTAL 水平影線  
  
- HS_VERTICAL 垂直影線  
  
 如果*lbStyle*是 BS_PATTERN， *lbHatch*是定義的模式之點陣圖的控制代碼。 如果*lbStyle* BS_SOLID 或 BS_HOLLOW， *lbHatch*會被忽略。  
  
## <a name="remarks"></a>備註  
 雖然*lbColor*控制規劃筆刷的前景色彩[CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode)並[CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor)函式會控制的背景色彩。  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

