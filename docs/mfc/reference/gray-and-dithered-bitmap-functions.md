---
title: 灰色和遞色點陣圖函式
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: bbc64aad0d65c0430ad23b96f635be8fe2b396e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357046"
---
# <a name="gray-and-dithered-bitmap-functions"></a>灰色和遞色點陣圖函式

**灰色點陣圖函式**

MFC 提供兩個函式來提供點陣圖已停用控制項的外觀。

![灰色和原本圖示版本的比較](../../mfc/reference/media/vcgraybitmap.gif "灰色和原本圖示版本的比較")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|繪製點陣圖的灰色版本。|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|複製點陣圖的灰色版本。|

**遞色點陣圖函式**

MFC 也提供兩個函式將點陣圖的背景取代為遞色圖樣。

![遞色和原本圖示版本的比較](../../mfc/reference/media/vcditheredbitmap.gif "遞色和原本圖示版本的比較")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|繪製遞色背景的點陣圖。|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|複製遞色背景的點陣圖。|

## <a name="afxdrawgraybitmap"></a><a name="afxdrawgraybitmap"></a>AfxDraw灰色位圖

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

*X.*<br/>
目的地 x 座標。

*Y*<br/>
目的地 y 座標。

*rSrc*<br/>
來源點陣圖。

*cr 背景*<br/>
新的背景色彩 (通常是灰色，例如 COLOR_MENU)。

### <a name="remarks"></a>備註

使用 `AfxDrawGrayBitmap` 繪製的點陣圖，外觀為已停用的控制項。

![灰色和原本圖示版本的比較](../../mfc/reference/media/vcgraybitmap.gif "灰色和原本圖示版本的比較")

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="afxgetgraybitmap"></a><a name="afxgetgraybitmap"></a>AfxGet格雷比特圖

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

*cr 背景*<br/>
新的背景色彩 (通常是灰色，例如 COLOR_MENU)。

### <a name="remarks"></a>備註

使用 `AfxGetGrayBitmap` 複製的點陣圖，外觀上會有已停用的控制項。

![灰色和原本圖示版本的比較](../../mfc/reference/media/vcgraybitmap.gif "灰色和原本圖示版本的比較")

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="afxdrawditheredbitmap"></a><a name="afxdrawditheredbitmap"></a>AfxDrawDitheredBitmap

繪製點陣圖,將其背景替換為抖抖(跳棋)圖案。

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

*X.*<br/>
目的地 x 座標。

*Y*<br/>
目的地 y 座標。

*rSrc*<br/>
來源點陣圖。

*cr1*<br/>
兩個遞色色彩之一，通常為白色。

*cr2*<br/>
另一個遞色色彩，通常是淺灰色 (COLOR_MENU)。

### <a name="remarks"></a>備註

源點陣圖在目標 DC 上繪製,其雙色 *(cr1*和*cr2)* 格格模式取代了位圖的背景。 來源點陣圖的背景會定義為其白色像素，以及符合點陣圖左上角像素色彩的所有像素。

![遞色和原本圖示版本的比較](../../mfc/reference/media/vcditheredbitmap.gif "遞色和原本圖示版本的比較")

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="afxgetditheredbitmap"></a><a name="afxgetditheredbitmap"></a>AfxGetDitheredBitmap

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

源點圖以雙色 *(cr1*和*cr2)* 的方格模式複製到目標位圖,取代來源位圖的背景。 來源點陣圖的背景會定義為其白色像素，以及符合點陣圖左上角像素色彩的所有像素。

![遞色和原本圖示版本的比較](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
