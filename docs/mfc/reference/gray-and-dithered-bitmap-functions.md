---
title: "灰色和遞色點陣圖函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
dev_langs:
- C++
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7f895fb22e4f4d2649cdec1e4c9925b69b013e49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="gray-and-dithered-bitmap-functions"></a>灰色和遞色點陣圖函式
**灰色點陣圖函式**  
  
 MFC 提供兩個函式來提供點陣圖已停用控制項的外觀。  
  
 ![灰色和原本圖示版本的比較](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
|||  
|-|-|  
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|繪製點陣圖的灰色版本。|  
|[AfxGetGrayBitmap](#afxgetgraybitmap)|複製點陣圖的灰色版本。|  
  
 **遞色點陣圖函式**  
  
 MFC 也提供兩個函式將點陣圖的背景取代為遞色圖樣。  
  
 ![遞色和原本圖示版本的比較](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
|||  
|-|-|  
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|繪製遞色背景的點陣圖。|  
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|複製遞色背景的點陣圖。|  
  
##  <a name="afxdrawgraybitmap"></a>  AfxDrawGrayBitmap  
 繪製點陣圖的灰色版本。  
  
```   
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向目的地 DC。  
  
 *x*  
 目的地 x 座標。  
  
 *y*  
 目的地 y 座標。  
  
 `rSrc`  
 來源點陣圖。  
  
 `crBackground`  
 新的背景色彩 (通常是灰色，例如 COLOR_MENU)。  
  
### <a name="remarks"></a>備註  
 使用 `AfxDrawGrayBitmap` 繪製的點陣圖，外觀為已停用的控制項。  
  
 ![灰色和原本圖示版本的比較](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]  

### <a name="requirements"></a>需求  
 **標題:** afxwin.h  

##  <a name="afxgetgraybitmap"></a>  AfxGetGrayBitmap  
 複製點陣圖的灰色版本。  
  
```   
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF crBackground); 
```  
  
### <a name="parameters"></a>參數  
 `rSrc`  
 來源點陣圖。  
  
 `pDest`  
 目的點陣圖。  
  
 `crBackground`  
 新的背景色彩 (通常是灰色，例如 COLOR_MENU)。  
  
### <a name="remarks"></a>備註  
 使用 `AfxGetGrayBitmap` 複製的點陣圖，外觀上會有已停用的控制項。  
  
 ![灰色和原本圖示版本的比較](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]  

### <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="afxdrawditheredbitmap"></a>  AfxDrawDitheredBitmap  
 繪製點陣圖，以遞色 （檢查程式） 樣式取代它的背景。  
  
```   
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,  
    int x,  
    int y,  
    const CBitmap& rSrc,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指向目的地 DC。  
  
 *x*  
 目的地 x 座標。  
  
 *y*  
 目的地 y 座標。  
  
 `rSrc`  
 來源點陣圖。  
  
 `cr1`  
 兩個遞色色彩之一，通常為白色。  
  
 `cr2`  
 另一個遞色色彩，通常是淺灰色 (COLOR_MENU)。  
  
### <a name="remarks"></a>備註  
 含有兩個色彩的目的地 DC 上繪製的來源點陣圖 (`cr1`和`cr2`) 棋盤式的圖樣取代點陣圖的背景。 來源點陣圖的背景會定義為其白色像素，以及符合點陣圖左上角像素色彩的所有像素。  
  
 ![遞色和原本圖示版本的比較](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]  

### <a name="requirements"></a>需求  
 **標題:** afxwin.h  


##  <a name="afxgetditheredbitmap"></a>  AfxGetDitheredBitmap  
 複製點陣圖，以遞色 (檢查程式) 樣式取代它的背景。  
  
```   
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,  
    CBitmap* pDest,  
    COLORREF cr1  ,  
    COLORREF cr2); 
```  
  
### <a name="parameters"></a>參數  
 `rSrc`  
 來源點陣圖。  
  
 `pDest`  
 目的點陣圖。  
  
 `cr1`  
 兩個遞色色彩之一，通常為白色。  
  
 `cr2`  
 另一個遞色色彩，通常是淺灰色 (COLOR_MENU)。  
  
### <a name="remarks"></a>備註  
 將來源點陣圖複製到目的地點陣圖與兩個色彩 (`cr1`和`cr2`) 棋盤式的圖樣取代來源點陣圖的背景。 來源點陣圖的背景會定義為其白色像素，以及符合點陣圖左上角像素色彩的所有像素。  
  
 ![遞色和原本圖示版本的比較](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]  

### <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
