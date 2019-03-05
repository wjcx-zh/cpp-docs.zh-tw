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
ms.openlocfilehash: 70329d3b2c18c8cd8e94854f40ff971c0b39a8f4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301814"
---
# <a name="atldrawinfo-structure"></a>ATL_DRAWINFO 結構

包含用於轉譯成各種不同的目標，例如印表機、 中繼檔或 ActiveX 控制項的資訊。

## <a name="syntax"></a>語法

```
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
結構，以位元組為單位的大小。

`dwDrawAspect`<br/>
指定目標是要表示的方式。 表示可以包含內容、 圖示、 縮圖或列印的文件。 如需可能值的清單，請參閱 < [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect)並[DVASPECT2](/windows/desktop/api/ocidl/ne-ocidl-tagdvaspect2)。

`lindex`<br/>
目標進行繪製作業的相關部分。 它的解譯方式中的值而異`dwDrawAspect`成員。

`ptd`<br/>
指標[DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice)可根據指定的外觀的繪圖最佳化的結構。 請注意，較新的物件和支援最佳化的繪圖介面的容器支援以及這個成員。 較舊的物件和一律不支援最佳化的繪圖介面的容器指定這個成員為 NULL。

`hicTargetDev`<br/>
所指向的目標裝置的資訊內容`ptd`物件可以從中擷取裝置度量資訊，並測試裝置的功能。 如果`ptd`為 NULL，該物件應該忽略中的值`hicTargetDev`成員。

`hdcDraw`<br/>
在其上繪製的裝置內容。 無視窗的物件，如`hdcDraw`成員是在`MM_TEXT`對應模式比對包含視窗的用戶端座標其邏輯座標。 此外，裝置內容應該在相同的狀態是通常傳遞`WM_PAINT`訊息。

`prcBounds`<br/>
指標[RECTL](https://msdn.microsoft.com/library/windows/desktop/dd162907)結構，指定矩形上`hdcDraw`，在應該繪製的物件。 這個成員控制項的定位和延伸的物件。 這個成員應該是 NULL，來繪製無視窗的就地使用中的物件。 在每個其他情況下，NULL 不是合法的值，並應該會導致`E_INVALIDARG`錯誤碼。 如果容器會將非 NULL 值傳遞至無視窗的物件，該物件應該轉譯要求的長寬成指定的裝置內容和矩形。 容器可以要求從無視窗物件來呈現物件的第二個 」、 「 非作用中的檢視，或列印物件。

`prcWBounds`<br/>
如果`hdcDraw`中繼檔裝置內容 (請參閱 < [GetDeviceCaps](/windows/desktop/api/wingdi/nf-wingdi-getdevicecaps) Windows SDK 中)，這是一個指向`RECTL`結構基礎中繼檔中指定的週框。 矩形結構包含視窗範圍和視窗原點。 這些值可用於繪製中繼檔。 所表示的矩形`prcBounds`在此為巢狀`prcWBounds`矩形; 它們是相同的座標空間中。

`bOptimize`<br/>
如果控制項的繪圖是要最佳化，否則為 0，非零值。 當您完成時，如果最佳化的繪圖，就會自動還原裝置內容的狀態呈現。

`bZoomed`<br/>
如果目標有縮放因數，否則為 0，非零值。 縮放因數會儲存在`ZoomNum`。

`bRectInHimetric`<br/>
非零的尺寸`prcBounds`位於 HIMETRIC，否則為 0。

`ZoomNum`<br/>
寬度和轉譯之物件的矩形的高度。 縮放因數，沿著 x 軸 （其目前的範圍內的物件的原始大小比例） 的目標是 windows 7`ZoomNum.cx`的值來分割`ZoomDen.cx`。 沿 y 軸的縮放因數是以類似的方式來達成。

`ZoomDen`<br/>
實際寬度和高度的目標。

## <a name="remarks"></a>備註

此結構的典型用法就是資訊的擷取期間的目標物件呈現。 例如，您可以從 ATL_DRAWINFO 擷取值內您多載[CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。

此結構會儲存用來呈現物件的目標裝置之外觀的相關資訊。 提供的資訊可以用於繪製到螢幕、 印表機或甚至在中繼檔。

## <a name="requirements"></a>需求

**標頭：** atlctl.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
