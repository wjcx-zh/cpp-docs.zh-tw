---
title: BITMAPINFO 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAPINFO
dev_langs:
- C++
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bc5adbb62e70a012d9dff4f9a390a46476aaa36
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200252"
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO 結構
`BITMAPINFO`結構會定義維度和 Windows 裝置獨立點陣圖 (DIB) 的色彩資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>參數  
 *bmiHeader*  
 指定[BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)結構，包含維度與裝置無關點陣圖的色彩格式的相關資訊。  
  
 *bmiColors*  
 指定的陣列[RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)或 DWORD 定義色彩點陣圖中的資料類型。  
  
## <a name="remarks"></a>備註  
 裝置獨立點陣圖是由兩個不同的部分所組成：`BITMAPINFO`該結構描述的維度和 色彩的點陣圖，並指定像素的點陣圖中的位元組陣列。 陣列中的位元會封裝在一起，但必須以結束日的零填補每一條掃描線**長**界限。 如果高度是正數，點陣圖的來源是左下角。 如果高度為負數，原點是左上角。  
  
 A*壓縮的點陣圖*是立即遵循的位元組陣列的點陣圖`BITMAPINFO`結構。 單一的指標會參考封裝的點陣圖。  
  
 如需詳細資訊`BITMAPINFO`結構，並適當值的成員`BITMAPINFOHEADER`和`RGBQUAD`結構，請參閱下列主題中的 Windows SDK 文件。  
  
- [BITMAPINFO 結構](/windows/desktop/api/wingdi/ns-wingdi-tagbitmapinfo)  
  
- [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)結構  
  
- [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)結構  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](https://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](/windows/desktop/api/wingdi/ns-wingdi-tagrgbquad)

