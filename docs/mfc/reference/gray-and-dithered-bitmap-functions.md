---
title: 灰色和遞色點陣圖函式
ms.date: 11/04/2016
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: 1134cde55fbe5addac34b9c0433ff11df4c9bdc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490892"
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

*pDC*<br/>
指向目的地 DC。

*x*<br/>
目的地 x 座標。

*y*<br/>
目的地 y 座標。

*rSrc*<br/>
來源點陣圖。

*crBackground*<br/>
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

*rSrc*<br/>
來源點陣圖。

*pDest*<br/>
目的點陣圖。

*crBackground*<br/>
新的背景色彩 (通常是灰色，例如 COLOR_MENU)。

### <a name="remarks"></a>備註

使用 `AfxGetGrayBitmap` 複製的點陣圖，外觀上會有已停用的控制項。

![灰色和原本圖示版本的比較](../../mfc/reference/media/vcgraybitmap.gif "vcgraybitmap")

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="afxdrawditheredbitmap"></a>  AfxDrawDitheredBitmap

繪製點陣圖，它的背景取代為遞色 （檢查程式） 模式。

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

*pDC*<br/>
指向目的地 DC。

*x*<br/>
目的地 x 座標。

*y*<br/>
目的地 y 座標。

*rSrc*<br/>
來源點陣圖。

*cr1*<br/>
兩個遞色色彩之一，通常為白色。

*cr2*<br/>
另一個遞色色彩，通常是淺灰色 (COLOR_MENU)。

### <a name="remarks"></a>備註

含有兩個色彩的目的地 DC 上繪製的來源點陣圖 (*cr1*並*cr2*) 棋盤式的圖樣取代點陣圖的背景。 來源點陣圖的背景會定義為其白色像素，以及符合點陣圖左上角像素色彩的所有像素。

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

*rSrc*<br/>
來源點陣圖。

*pDest*<br/>
目的點陣圖。

*cr1*<br/>
兩個遞色色彩之一，通常為白色。

*cr2*<br/>
另一個遞色色彩，通常是淺灰色 (COLOR_MENU)。

### <a name="remarks"></a>備註

來源點陣圖複製到目的地點陣圖與兩個色彩 (*cr1*並*cr2*) 棋盤式的圖樣，取代來源點陣圖的背景。 來源點陣圖的背景會定義為其白色像素，以及符合點陣圖左上角像素色彩的所有像素。

![遞色和原本圖示版本的比較](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
