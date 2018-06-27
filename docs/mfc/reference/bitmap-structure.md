---
title: 點陣圖結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a60e4af31ba5da23f399f86175ed4fcf1e4ec14
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950299"
---
# <a name="bitmap-structure"></a>BITMAP 結構
**點陣圖**結構會定義高度、 寬度、 色彩格式和位元值的邏輯點陣圖 **。**  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagBITMAP {  /* bm */  
    int bmType;  
    int bmWidth;  
    int bmHeight;  
    int bmWidthBytes;  
    BYTE bmPlanes;  
    BYTE bmBitsPixel;  
    LPVOID bmBits;  
} BITMAP;  
```  
  
#### <a name="parameters"></a>參數  
 *bmType*  
 指定點陣圖類型。 在邏輯點陣圖中，此成員必須是 0。  
  
 *bmWidth*  
 以像素為單位指定點陣圖的寬度。 寬度必須大於 0。  
  
 *bmHeight*  
 以光柵行為單位指定點陣圖的高度。 高度必須大於 0。  
  
 *bmWidthBytes*  
 指定每個光柵行的位元組數。 這個值必須是偶數，因為繪圖裝置介面 (GDI) 會假設點陣圖格式的位元值為整數 (2 位元組) 值陣列。 換句話說， *bmWidthBytes* \* 8 必須是下一個 16 的倍數大於或等於值時，取得*bmWidth*成員乘以*bmBitsPixel*成員。  
  
 *bmPlanes*  
 指定點陣圖中色彩平面的數目。  
  
 *bmBitsPixel*  
 在定義像素所需的每個平面上指定相鄰色彩位元數量。  
  
 *bmBits*  
 指向點陣圖中位元值的位置。 *BmBits*成員必須是 1 位元組值陣列的長指標。  
  
## <a name="remarks"></a>備註  
 目前所使用的點陣圖格式為單色和彩色。 單色點陣圖使用 1 位元 1 平面格式。 每個掃描的位元組皆為 16 的倍數。  
  
 掃描編排，如下所示的單色點陣圖的高度*n*:  
  
 `Scan 0`  
  
 `Scan 1`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 `Scan n-2`  
  
 `Scan n-1`  
  
 在單色裝置上的像素不是黑色就是白色。 如果在點陣圖中對應的位元為 1，則像素已開啟 (白色)。 如果在點陣圖中對應的位元為 0，則像素會關閉 (黑色)。  
  
 所有裝置都支援的點陣圖， **RC_BITBLT**中設定位元**cdc:: GETDEVICECAPS**索引[rastercaps](../../mfc/reference/cdc-class.md#getdevicecaps)成員函式。  
  
 每個裝置有其獨特的色彩格式。 若要將點陣圖從一個裝置傳送到另一個，使用[GetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd144879)和[SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) Windows 函式。  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Bitmap](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
