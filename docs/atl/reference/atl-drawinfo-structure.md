---
title: ATL_DRAWINFO結構
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: fb50f49d387e8620f3d5bbb41263738adbd8b437
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748799"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO結構

包含用於呈現到各種目標(如印表機、元檔或 ActiveX 控制件)的資訊。

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
結構的大小(以位元組為單位)。

`dwDrawAspect`<br/>
指定如何表示目標。 表示可以包括內容、圖示、縮略圖或列印的文檔。 有關可能值的清單,請參閱[DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)與[DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2)。

`lindex`<br/>
對繪製操作感興趣的目標部分。 其解釋因`dwDrawAspect`成員中的值而異。

`ptd`<br/>
指向[DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice)結構的指標,該結構可根據指定的方面進行繪製優化。 請注意,支援優化繪圖介面的較新的物件和容器也支援此成員。 不支援最佳化繪圖介面的舊物件和容器始終為此成員指定 NULL。

`hicTargetDev`<br/>
指向的目標設備的資訊上下文,物件可以從`ptd`中提取設備指標並測試設備的功能。 如果`ptd`為 NULL,則物件應忽略成員`hicTargetDev`中的值。

`hdcDraw`<br/>
要繪製的設備上下文。 對於無視窗物件,`hdcDraw`成員`MM_TEXT`處於映射模式,其邏輯座標與包含視窗的用戶端座標匹配。 此外,設備上下文應處於與通常通過`WM_PAINT`消息傳遞的狀態相同的狀態。

`prcBounds`<br/>
指向[RECTL](/windows/win32/api/windef/ns-windef-rectl)結構的指標,`hdcDraw`指定在上和其中繪製物件的矩形。 此成員控制物件的定位和拉伸。 此成員應為 NULL,以繪製無視窗就地活動物件。 在所有其他情況下,NULL 不是法律價值,應`E_INVALIDARG`會導致錯誤代碼。 如果容器將非 NULL 值傳遞給無視窗物件,則該物件應將請求的方面呈現為指定的設備上下文和矩形。 容器可以從無視窗物件請求此檢視以呈現物件的第二個非活動視圖或列印該物件。

`prcWBounds`<br/>
如果是`hdcDraw`元文件設備上下文(請參閱 Windows SDK 中的[GetDeviceCaps),](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps)`RECTL`則這是指向在基礎 中檔中指定邊界矩形的結構的指標。 矩形結構包含視窗範圍和視窗原點。 這些值可用於繪製元檔。 表示的矩形嵌套`prcBounds`在此矩形內;`prcWBounds`如果 位於此矩形內,則表示的矩形位於此矩形內。它們位於同一座標空間中。

`bOptimize`<br/>
如果要優化控件的圖形,則非零,否則為 0。 如果繪圖已優化,則完成渲染后,將自動還原設備上下文的狀態。

`bZoomed`<br/>
如果目標具有縮放係數,則非零,否則為 0。 縮放係數儲存在中`ZoomNum`。

`bRectInHimetric`<br/>
如果的`prcBounds`尺寸在 HIMETRIC 中,則非零,否則為 0。

`ZoomNum`<br/>
對象呈現到的矩形的寬度和高度。 沿目標的 x 軸(物件的自然大小與其當前範圍的比例)的縮放係`ZoomNum.cx`數是 除以`ZoomDen.cx`的值。 沿 y 軸的縮放係數以類似方式實現。

`ZoomDen`<br/>
目標的實際寬度和高度。

## <a name="remarks"></a>備註

此結構的典型用法是在呈現目標對象期間檢索資訊。 例如,可以從 CcomControlBase 的重載中從ATL_DRAWINFO檢索值[:onDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced)。

此結構存儲用於呈現目標設備物件外觀的相關信息。 提供的資訊可用於繪製到螢幕、印表機甚至元檔。

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="see-also"></a>另請參閱

[類別和結構](../../atl/reference/atl-classes.md)<br/>
[IView物件::D原始](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase:OnDraw高級](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
