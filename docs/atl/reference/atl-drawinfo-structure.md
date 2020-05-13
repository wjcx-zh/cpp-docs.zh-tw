---
title: ATL_DRAWINFO 結構
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 00d93b3dd8b060a21b6ff4083bb9880d8d836a19
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168614"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO 結構

包含用來轉譯成各種目標的資訊，例如印表機、中繼檔或 ActiveX 控制項。

## <a name="syntax"></a>語法

```cpp
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```

## <a name="members"></a>成員

`cbSize`<br/>
結構的大小（以位元組為單位）。

`dwDrawAspect`<br/>
指定要如何表示目標。 標記法可以包含內容、圖示、縮圖或列印檔案。 如需可能值的清單，請參閱[DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)和[DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2)。

`lindex`<br/>
繪製作業的相關目標部分。 其轉譯會根據`dwDrawAspect`成員中的值而有所不同。

`ptd`<br/>
[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)結構的指標，可根據指定的外觀啟用繪製優化。 請注意，支援優化繪圖介面的較新物件和容器也支援此成員。 較舊的物件和不支援優化繪圖介面的容器，一律會為這個成員指定 Null。

`hicTargetDev`<br/>
目標裝置`ptd`的資訊內容，物件可以從中解壓縮裝置計量並測試裝置的功能。 如果`ptd`為 Null，則物件應忽略`hicTargetDev`成員中的值。

`hdcDraw`<br/>
要在其上繪製的裝置內容。 對於無視窗物件， `hdcDraw`成員是在`MM_TEXT`對應模式中，其邏輯座標符合包含視窗的用戶端座標。 此外，裝置內容的狀態應該與一般由`WM_PAINT`訊息傳遞的相同。

`prcBounds`<br/>
[RECTL](/windows/win32/api/windef/ns-windef-rectl)結構的指標，指定在和上`hdcDraw`應該繪製物件的矩形。 這個成員控制物件的定位和延展。 這個成員應該是 Null，才能繪製無視窗的就地作用中物件。 在其他所有情況下，Null 不是合法的值，而且應該會`E_INVALIDARG`產生錯誤碼。 如果容器將非 Null 值傳遞給無視窗物件，物件應該會將要求的外觀轉譯為指定的裝置內容和矩形。 容器可以從無視窗物件要求此項，以轉譯物件的第二個非現用視圖，或列印物件。

`prcWBounds`<br/>
如果`hdcDraw`是中繼檔裝置內容（請參閱 Windows SDK 中的[GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) ），這是`RECTL`結構的指標，指定基礎中繼檔中的周框。 矩形結構包含視窗範圍和視窗原點。 這些值適用于繪製中繼檔。 所表示的矩形`prcBounds`會嵌套在這個`prcWBounds`矩形內;它們在相同的座標空間中。

`bOptimize`<br/>
如果要優化控制項的繪製，則為非零，否則為0。 如果繪圖已優化，則當您完成轉譯時，會自動還原裝置內容的狀態。

`bZoomed`<br/>
如果目標具有縮放因數，則為非零，否則為0。 縮放因數會儲存在中`ZoomNum`。

`bRectInHimetric`<br/>
如果的維度`prcBounds`位於 HIMETRIC 中，則為非零，否則為0。

`ZoomNum`<br/>
呈現物件之矩形的寬度和高度。 目標的縮放因數沿著 X 軸（物件的自然大小和其目前範圍的比例）是值`ZoomNum.cx`除以的值。 `ZoomDen.cx` 沿著 y 軸的縮放因數是以類似的方式來達成。

`ZoomDen`<br/>
目標的實際寬度和高度。

## <a name="remarks"></a>備註

此結構的一般用法是在轉譯目標物件期間的資訊的抓取。 例如，您可以從[CComControlBase：： OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)的多載內，抓取 ATL_DRAWINFO 的值。

這個結構會儲存用來呈現目標裝置之物件外觀的相關資訊。 提供的資訊可用於繪製到螢幕、印表機，甚至是中繼檔。

## <a name="requirements"></a>需求

**標頭：** atlctl。h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)<br/>
[IViewObject：:D raw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
