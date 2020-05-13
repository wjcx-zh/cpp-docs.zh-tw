---
title: CStockPropimpl 類別
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: 0aaeb1b6de0febfd5fc0d41cbcc7bad41c607af4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330665"
---
# <a name="cstockpropimpl-class"></a>CStockPropimpl 類別

此類提供支援股票屬性值的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <
    class T,
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>參數

*T*<br/>
實現控制項並從 派生的`CStockPropImpl`類別 。

*介面名稱*<br/>
公開股票屬性的雙介面。

*皮伊德*<br/>
指向 IID`InterfaceName`的指標。

*普利比德*<br/>
指向類型庫的 LIBID 的指標,其中`InterfaceName`包含的定義。

*w 主要*<br/>
類型程式庫的主要版本。 預設值為 1。

*wMinor*<br/>
類型程式庫的次要版本。 預設值為 0。

*提赫班*<br/>
用於管理*T*的類型資訊的類。預設值為`CComTypeInfoHolder`。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|||
|-|-|
|[get_Appearance](#get_appearance)|呼叫此方法獲取控制件使用的繪製樣式,例如平面或 3D。|
|[get_AutoSize](#get_autosize)|呼叫此方法以獲取指示控制項是否不能為任何其他大小的標誌的狀態。|
|[get_BackColor](#get_backcolor)|呼叫此方法以獲取控制項的背景顏色。|
|[get_BackStyle](#get_backstyle)|呼叫此方法獲取控制項的背景樣式,無論是透明還是不透明。|
|[get_BorderColor](#get_bordercolor)|呼叫此方法以獲取控制項的邊框顏色。|
|[get_BorderStyle](#get_borderstyle)|調用此方法以獲取控制項的邊框樣式。|
|[get_BorderVisible](#get_bordervisible)|調用此方法以獲取指示控制項的邊框是否可見的標誌的狀態。|
|[get_BorderWidth](#get_borderwidth)|調用此方法獲取控制項邊框的寬度(以像素為單位)。|
|[get_Caption](#get_caption)|呼叫此方法以取得物件標題中指定的文字。|
|[get_DrawMode](#get_drawmode)|呼叫此方法以取得控制項的繪圖模式,例如 XOR 筆或反轉顏色。|
|[get_DrawStyle](#get_drawstyle)|呼叫此方法獲取控制項的繪圖樣式,例如,實體、虛線或虛線。|
|[get_DrawWidth](#get_drawwidth)|調用此方法以獲取控制項的繪圖方法使用的繪圖寬度(以圖元為單位)。|
|[get_Enabled](#get_enabled)|呼叫此方法以獲取指示控制項是否已啟用的標誌的狀態。|
|[get_FillColor](#get_fillcolor)|呼叫此方法以獲取控制項的填充顏色。|
|[get_FillStyle](#get_fillstyle)|調用此方法獲取控件的填充樣式,例如,實心、透明或交叉陰影。|
|[get_Font](#get_font)|調用此方法以獲取指向控制項的字體屬性的指標。|
|[get_ForeColor](#get_forecolor)|調用此方法以獲取控制項的前景顏色。|
|[get_HWND](#get_hwnd)|調用此方法以獲取與控制項關聯的視窗句柄。|
|[get_MouseIcon](#get_mouseicon)|調用此方法以取得滑鼠位於控制項上時要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性。|
|[get_MousePointer](#get_mousepointer)|調用此方法可獲取滑鼠位於控件(例如箭頭、交叉或沙漏)上時顯示的滑鼠指標類型。|
|[get_Picture](#get_picture)|呼叫此方法以取得指向要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性的指標。|
|[get_ReadyState](#get_readystate)|調用此方法以獲取控制項的就緒狀態,例如載入或載入。|
|[get_TabStop](#get_tabstop)|調用此方法以獲取指示控制項是否為製表位標誌的標誌。|
|[get_Text](#get_text)|呼叫此方法取得控制項中顯示的文字。|
|[取得有效](#get_valid)|調用此方法以獲取指示控制項是否有效的標誌的狀態。|
|[get_Window](#get_window)|調用此方法以獲取與控制項關聯的視窗句柄。 與[CStockPropImpl 相同:get_HWND](#get_hwnd)。|
|[put_Appearance](#put_appearance)|呼叫此方法以設置控制項使用的繪製樣式,例如平面或 3D。|
|[put_AutoSize](#put_autosize)|調用此方法以設置指示控制項不能為任何其他大小的標誌的值。|
|[put_BackColor](#put_backcolor)|呼叫此方法以設定控制項的背景顏色。|
|[put_BackStyle](#put_backstyle)|調用此方法以設置控制項的背景樣式。|
|[put_BorderColor](#put_bordercolor)|調用此方法以設置控制項的邊框顏色。|
|[put_BorderStyle](#put_borderstyle)|調用此方法以設置控制件的邊框樣式。|
|[put_BorderVisible](#put_bordervisible)|呼叫此方法以設定指示控制項的邊框是否可見的標誌的值。|
|[put_BorderWidth](#put_borderwidth)|調用此方法以設置控制式邊框的寬度。|
|[put_Caption](#put_caption)|呼叫此方法以將要與控制項一起顯示的文本設置為"|
|[put_DrawMode](#put_drawmode)|呼叫此方法以設定控制項的繪圖模式,例如 XOR 筆或反轉顏色。|
|[put_DrawStyle](#put_drawstyle)|調用此方法以設置控制項的繪圖樣式,例如,實體、虛線或虛線。|
|[put_DrawWidth](#put_drawwidth)|調用此方法以設置控制項的繪圖方法使用的寬度(以像素為單位)。|
|[put_Enabled](#put_enabled)|調用此方法以設置指示控制項是否已啟用的標誌。|
|[put_FillColor](#put_fillcolor)|調用此方法以設置控制項的填充顏色。|
|[put_FillStyle](#put_fillstyle)|調用此方法以設置控制項的填充樣式,例如,實心、透明或交叉陰影。|
|[put_Font](#put_font)|調用此方法以設置控制項的字體屬性。|
|[put_ForeColor](#put_forecolor)|調用此方法以設置控制項的前景顏色。|
|[put_HWND](#put_hwnd)|此方法返回E_FAIL。|
|[put_MouseIcon](#put_mouseicon)|調用此方法可設置滑鼠位於控制項上時要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性。|
|[put_MousePointer](#put_mousepointer)|調用此方法可設置滑鼠位於控件上時顯示的滑鼠指標類型,例如箭頭、十字或沙漏。|
|[put_Picture](#put_picture)|呼叫此方法以設定要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性。|
|[put_ReadyState](#put_readystate)|調用此方法以設置控制項的就緒狀態,例如載入或載入。|
|[put_TabStop](#put_tabstop)|調用此方法以設置指示控制項是否為製表位的標誌的值。|
|[put_Text](#put_text)|呼叫此方法以設定控制項中顯示的文字。|
|[放有效](#put_valid)|調用此方法以設置指示控制項是否有效的標誌。|
|[put_Window](#put_window)|此方法稱為[CStock Propimpl::put_HWND](#put_hwnd),它返回E_FAIL。|
|[putref_Font](#putref_font)|調用此方法以設置控制項的字型屬性,並帶有引用計數。|
|[putref_MouseIcon](#putref_mouseicon)|調用此方法可設置滑鼠位於控件上時要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性,並帶有引用計數。|
|[putref_Picture](#putref_picture)|調用此方法以設置要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性,並帶有引用計數。|

## <a name="remarks"></a>備註

`CStockPropImpl`為每個股票屬性提供**放和****獲取**方法。 這些方法提供了必要的代碼,用於設置或獲取與每個屬性關聯的數據成員,並在任何屬性發生更改時通知容器並與容器同步。

Visual Studio 通過其嚮導支援股票屬性。 有關向控制項添加股票屬性的詳細資訊,請參閱[ATL 教程](../../atl/active-template-library-atl-tutorial.md)。

對於向後相容性,`CStockPropImpl`還`get_Window`公開`put_Window`和`get_HWND`分別`put_HWND`調用 和 的方法。 由於 HWND 應該是唯讀屬性,因此`put_HWND`返回的 預設實現E_FAIL。

以下屬性還具有**putref**實現:

- 字型

- 滑鼠圖示

- Picture

相同的三個庫存屬性要求其相應的數據成員的類型`CComPtr`或其他一些類通過賦值運算符提供正確的介面引用計數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>需求

**標題:** atlctl.h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropimpl:get_Appearance

呼叫此方法獲取控制件使用的繪製樣式,例如平面或 3D。

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>參數

*pn外觀*<br/>
接收控件的繪製樣式的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropimpl::get_AutoSize

呼叫此方法以獲取指示控制項是否不能為任何其他大小的標誌的狀態。

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>參數

*pb 自動大小*<br/>
接收標誌狀態的變數。 TRUE 表示控件不能是任何其他大小。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropimpl::get_BackColor

呼叫此方法以獲取控制項的背景顏色。

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>參數

*pclrBackColor*<br/>
接收控制項背景顏色的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropimpl::get_BackStyle

呼叫此方法獲取控制項的背景樣式,無論是透明還是不透明。

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>參數

*pnBackStyle*<br/>
接收控制項的背景樣式的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropimpl::get_BorderColor

呼叫此方法以獲取控制項的邊框顏色。

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>參數

*pclr 邊框顏色*<br/>
接收控件邊框顏色的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropimpl::get_BorderStyle

調用此方法以獲取控制項的邊框樣式。

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>參數

*pn邊框樣式*<br/>
接收控件邊框樣式的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropimpl:get_BorderVisible

調用此方法以獲取指示控制項的邊框是否可見的標誌的狀態。

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>參數

*pb 邊界可見*<br/>
接收標誌狀態的變數。 TRUE 表示控件的邊框可見。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropimpl:get_BorderWidth

調用此方法獲取控件邊框的寬度。

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>參數

*pn邊框寬度*<br/>
接收控件的邊框寬度的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropimpl:get_Caption

呼叫此方法以取得物件標題中指定的文字。

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>參數

*pbstrCaption*<br/>
要與控制項一起顯示的文本。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropimpl:get_DrawMode

呼叫此方法以取得控制項的繪圖模式,例如 XOR 筆或反轉顏色。

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>參數

*pnDraw模式*<br/>
接收控件的繪圖模式的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropimpl:get_DrawStyle

呼叫此方法獲取控制項的繪圖樣式,例如,實體、虛線或虛線。

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>參數

*pnDraw樣式*<br/>
接收控件的繪圖樣式的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropimpl:get_DrawWidth

調用此方法以獲取控制項的繪圖方法使用的繪圖寬度(以圖元為單位)。

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>參數

*pnDraw 寬度*<br/>
接收控件寬度值(以像素為單位)的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropimpl:get_Enabled

呼叫此方法以獲取指示控制項是否已啟用的標誌的狀態。

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>參數

*pb 啟用*<br/>
接收標誌狀態的變數。 TRUE 表示控件已啟用。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropimpl:get_FillColor

呼叫此方法以獲取控制項的填充顏色。

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>參數

*pclr 填充顏色*<br/>
接收控件填充顏色的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropimpl:get_FillStyle

調用此方法獲取控件的填充樣式,例如,實心、透明或交叉填充。

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>參數

*pn 填滿樣式*<br/>
接收控件填充樣式的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropimpl::get_Font

調用此方法以獲取指向控制項的字體屬性的指標。

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
接收指向控制字體屬性的指標的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropimpl:get_ForeColor

調用此方法以獲取控制項的前景顏色。

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>參數

*pclrForeColor*<br/>
接收控件前景顏色的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropimpl::get_HWND

調用此方法以獲取與控制項關聯的視窗句柄。

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>參數

*phwnd*<br/>
與控制項關聯的視窗句柄。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropimpl:get_MouseIcon

調用此方法以取得滑鼠位於控制項上時要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性。

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>參數

*ppPicture*<br/>
接收指向圖形圖片屬性的指標的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropimpl::get_MousePointer

調用此方法可獲取滑鼠位於控件(例如箭頭、交叉或沙漏)上時顯示的滑鼠指標類型。

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>參數

*pnMousePointer*<br/>
接收滑鼠指標類型的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropimpl::get_Picture

呼叫此方法以取得指向要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性的指標。

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>參數

*ppPicture*<br/>
接收指向圖片屬性的指標的變數。 有關詳細資訊[,請參閱 IPictureDisp。](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropimpl:get_ReadyState

調用此方法以獲取控制項的就緒狀態,例如載入或載入。

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>參數

*pnReadyState*<br/>
接收控件就緒狀態的變數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropimpl:get_TabStop

調用此方法以獲取指示控制項是否為製表位的標誌的狀態。

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>參數

*pbTabStop*<br/>
接收標誌狀態的變數。 TRUE 表示控件是製表位。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropimpl::get_Text

呼叫此方法取得控制項中顯示的文字。

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>參數

*pbstrText*<br/>
控制項顯示的文字。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropimpl::取得有效

調用此方法以獲取指示控制項是否有效的標誌的狀態。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>參數

*pb 有效*<br/>
接收標誌狀態的變數。 TRUE 表示控件有效。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropimpl:get_Window

調用此方法以獲取與控制項關聯的視窗句柄。 與[CStockPropImpl 相同:get_HWND](#get_hwnd)。

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>參數

*phwnd*<br/>
與控制項關聯的視窗句柄。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropimpl::put_外觀

呼叫此方法以設置控制項使用的繪製樣式,例如平面或 3D。

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>參數

*n 外觀*<br/>
控件將使用的新繪製樣式。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropimpl::put_自動大小

調用此方法以設置指示控制項不能為任何其他大小的標誌的值。

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>參數

*b 自動大小*<br/>
如果控件不能是任何其他大小,則為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropimpl::put_背面顏色

呼叫此方法以設定控制項的背景顏色。

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>參數

*clrBackColor*<br/>
新的控制項背景顏色。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropimpl::put_背面風格

調用此方法以設置控制項的背景樣式。

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>參數

*nBack 樣式*<br/>
新的控件背景樣式。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropimpl::put_邊框顏色

調用此方法以設置控制項的邊框顏色。

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>參數

*clrBorderColor*<br/>
新的邊框顏色。 OLE_COLOR數據類型在內部表示為 32 位長整數。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropimpl::put_邊框風格

調用此方法以設置控制件的邊框樣式。

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>參數

*n邊框樣式*<br/>
新的邊框樣式。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropimpl::put_邊界可見

呼叫此方法以設定指示控制項的邊框是否可見的標誌的值。

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>參數

*b 邊界可見*<br/>
如果邊框為可見,則為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropimpl::put_邊界寬度

調用此方法以設置控制式邊框的寬度。

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>參數

*n 邊框寬度*<br/>
控件邊框的新寬度。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropimpl::put_標題

呼叫此方法以將要與控制項一起顯示的文本設置為"

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>參數

*bstrCaption*<br/>
要與控制項一起顯示的文本。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropimpl::put_DrawMode

呼叫此方法以設定控制項的繪圖模式,例如 XOR 筆或反轉顏色。

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>參數

*nDrawMode*<br/>
控件的新繪圖模式。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropimpl::put_DrawStyle

調用此方法以設置控制項的繪圖樣式,例如,實體、虛線或虛線。

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>參數

*nDraw樣式*<br/>
控件的新繪圖樣式。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropimpl::put_DrawWidth

調用此方法以設置控制項的繪圖方法使用的寬度(以像素為單位)。

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>參數

*nDrawWidth*<br/>
控件的繪圖方法將使用的新寬度。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropimpl::put_啟用

呼叫此方法以設定指示控制項是否啟用的標誌的值。

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
如果啟用了控制項,則為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropimpl::put_FillColor

調用此方法以設置控制項的填充顏色。

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>參數

*clrFillColor*<br/>
控件的新填充顏色。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropimpl::put_FillStyle

調用此方法以設置控制項的填充樣式,例如,實心、透明或交叉陰影。

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>參數

*n 填滿樣式*<br/>
控件的新填充樣式。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropimpl::put_Font

調用此方法以設置控制項的字體屬性。

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
指向控件的字體屬性的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropimpl::put_前色

調用此方法以設置控制項的前景顏色。

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>參數

*clrForeColor*<br/>
控件的新前景顏色。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropimpl::put_HWND

此方法返回E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
已保留。

### <a name="return-value"></a>傳回值

返回E_FAIL。

### <a name="remarks"></a>備註

視窗句柄是唯讀值。

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropimpl::put_滑鼠圖示

調用此方法可設置滑鼠位於控制項上時要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性。

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*p 圖片*<br/>
指向圖形的圖片屬性的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropimpl::put_滑鼠指標

調用此方法可設置滑鼠位於控件上時顯示的滑鼠指標類型,例如箭頭、十字或沙漏。

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>參數

*nMousePointer*<br/>
滑鼠指標的類型。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropimpl::put_圖片

呼叫此方法以設定要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性。

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*p 圖片*<br/>
指向圖片屬性的指標。 有關詳細資訊[,請參閱 IPictureDisp。](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropimpl::put_就緒狀態

調用此方法以設置控制項的就緒狀態,例如載入或載入。

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>參數

*n 就緒狀態*<br/>
控件的就緒狀態。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropimpl::put_TabStop

調用此方法以設置指示控制項是否為製表位標誌的標誌。

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>參數

*bTabStop*<br/>
如果控件是製表位,則為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropimpl::put_文字

呼叫此方法以設定控制項中顯示的文字。

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>參數

*bstrText*<br/>
控制項顯示的文字。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropimpl::p

調用此方法以設置指示控制項是否有效的標誌。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>參數

*b 有效*<br/>
如果控件有效,則為 TRUE。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropimpl::put_視窗

此方法稱為[CStock Propimpl::put_HWND](#put_hwnd),它返回E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
視窗控制代碼 (Window Handle)。

### <a name="return-value"></a>傳回值

返回E_FAIL。

### <a name="remarks"></a>備註

視窗句柄是唯讀值。

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropimpl::putref_Font

調用此方法以設置控制項的字型屬性,並帶有引用計數。

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
指向控件的字體屬性的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

與[CStock PropImpl::put_Font](#put_font)相同,但具有參考計數。

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropimpl::putref_MouseIcon

調用此方法可設置滑鼠位於控件上時要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性,並帶有引用計數。

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*p 圖片*<br/>
指向圖形的圖片屬性的指標。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

與[CStock PropImpl::put_MouseIcon](#put_mouseicon)相同,但具有參考計數。

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl::p烏特雷夫_圖片

調用此方法以設置要顯示的圖形(圖示、點陣圖或元檔)的圖片屬性,並帶有引用計數。

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*p 圖片*<br/>
指向圖片屬性的指標。 有關詳細資訊[,請參閱 IPictureDisp。](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp)

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

與[CStockPropImpl::put_Picture)](#put_picture)相同,但具有參考計數。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)
