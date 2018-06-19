---
title: BITMAPINFO 結構 |Microsoft 文件
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
ms.openlocfilehash: e061802cbcd8926a146e5765cc9ecfd9bf917295
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348149"
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
 `bmiHeader`  
 指定[BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)結構，包含維度與裝置獨立點陣圖的色彩格式的相關資訊。  
  
 `bmiColors`  
 指定的陣列[RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)或`DWORD`定義色彩的點陣圖中的資料類型。  
  
## <a name="remarks"></a>備註  
 裝置獨立點陣圖是由兩個不同部分所組成：`BITMAPINFO`結構描述的維度和色彩的點陣圖的像素為單位指定點陣圖中的位元組陣列。 陣列中的位元會封裝在一起，但必須以每個掃描線填補零結束日`LONG`界限。 如果高度是正數，點陣圖的來源是左下角。 高度為負數，如果來源是左上角。  
  
 A*壓縮的點陣圖*是一種點陣圖，其中的位元組陣列緊接`BITMAPINFO`結構。 壓縮的點陣圖所參考的單一指標。  
  
 如需有關`BITMAPINFO`結構，並適當值的成員`BITMAPINFOHEADER`和`RGBQUAD`結構，請參閱 Windows SDK 的文件中的下列主題。  
  
- [BITMAPINFO 結構](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
- [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)結構  
  
- [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)結構  
  
## <a name="requirements"></a>需求  
 **標頭：** wingdi.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)

