---
title: CStockPropImpl 類別
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
ms.openlocfilehash: 9d54e4e5c49e73a12fc5d360c3963c2bcf5b2b38
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835580"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl 類別

此類別提供支援內建屬性值的方法。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

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
執行控制項並衍生自的類別 `CStockPropImpl` 。

*介面名稱*<br/>
公開股票屬性的雙重介面。

*piid*<br/>
的 IID 指標 `InterfaceName` 。

*plibid*<br/>
類型程式庫的 LIBID 的指標，其中包含的定義 `InterfaceName` 。

*wMajor*<br/>
類型程式庫的主要版本。 預設值為 1。

*wMinor*<br/>
類型程式庫的次要版本。 預設值為 0。

*tihclass*<br/>
用來管理 *T*類型資訊的類別。預設值為 `CComTypeInfoHolder` 。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[get_Appearance](#get_appearance)|呼叫這個方法以取得控制項所使用的繪製樣式，例如，平面或3D。|
|[get_AutoSize](#get_autosize)|呼叫這個方法，以取得指出控制項是否不能是任何其他大小的旗標狀態。|
|[get_BackColor](#get_backcolor)|呼叫這個方法來取得控制項的背景色彩。|
|[get_BackStyle](#get_backstyle)|呼叫這個方法來取得控制項的背景樣式，也就是透明或不透明。|
|[get_BorderColor](#get_bordercolor)|呼叫這個方法來取得控制項的框線色彩。|
|[get_BorderStyle](#get_borderstyle)|呼叫這個方法來取得控制項的框線樣式。|
|[get_BorderVisible](#get_bordervisible)|呼叫這個方法，以取得指出控制項框線是否可見的旗標狀態。|
|[get_BorderWidth](#get_borderwidth)|呼叫這個方法以取得控制項框線的寬度 (以圖元為單位) 。|
|[get_Caption](#get_caption)|呼叫這個方法，以取得物件標題中指定的文字。|
|[get_DrawMode](#get_drawmode)|呼叫這個方法來取得控制項的繪圖模式，例如 XOR 畫筆或反相顏色。|
|[get_DrawStyle](#get_drawstyle)|呼叫這個方法來取得控制項的繪製樣式，例如，實線、虛線或點線。|
|[get_DrawWidth](#get_drawwidth)|呼叫這個方法可取得控制項的繪圖方法所使用的繪圖寬度 (（以圖元為單位）) 。|
|[get_Enabled](#get_enabled)|呼叫這個方法，以取得指出是否已啟用控制項的旗標狀態。|
|[get_FillColor](#get_fillcolor)|呼叫這個方法來取得控制項的填滿色彩。|
|[get_FillStyle](#get_fillstyle)|呼叫這個方法來取得控制項的填滿樣式，例如，純色、透明或交叉影線。|
|[get_Font](#get_font)|呼叫這個方法，以取得控制項字型屬性的指標。|
|[get_ForeColor](#get_forecolor)|呼叫這個方法來取得控制項的前景色彩。|
|[get_HWND](#get_hwnd)|呼叫這個方法，以取得與控制項相關聯的視窗控制碼。|
|[get_MouseIcon](#get_mouseicon)|呼叫這個方法，取得圖形 (圖示、點陣圖或中繼檔的圖片屬性) 在滑鼠停留在控制項上時顯示。|
|[get_MousePointer](#get_mousepointer)|呼叫這個方法，以取得滑鼠停留在控制項上時所顯示的滑鼠指標類型，例如箭號、交叉或沙漏。|
|[get_Picture](#get_picture)|呼叫這個方法，取得圖形 (圖示、點陣圖或中繼檔的圖片屬性指標，) 要顯示的內容。|
|[get_ReadyState](#get_readystate)|呼叫這個方法以取得控制項的就緒狀態，例如載入或載入。|
|[get_TabStop](#get_tabstop)|呼叫這個方法來取得旗標，指出控制項是否為 tab 鍵停用。|
|[get_Text](#get_text)|呼叫這個方法來取得與控制項一起顯示的文字。|
|[getvalid](#get_valid)|呼叫這個方法，以取得指出控制項是否有效的旗標狀態。|
|[get_Window](#get_window)|呼叫這個方法，以取得與控制項相關聯的視窗控制碼。 與 [CStockPropImpl：： get_HWND](#get_hwnd)相同。|
|[put_Appearance](#put_appearance)|呼叫這個方法來設定控制項所使用的繪製樣式，例如，平面或3D。|
|[put_AutoSize](#put_autosize)|呼叫這個方法來設定旗標的值，這個值會指出控制項是否不能是任何其他大小。|
|[put_BackColor](#put_backcolor)|呼叫這個方法來設定控制項的背景色彩。|
|[put_BackStyle](#put_backstyle)|呼叫這個方法來設定控制項的背景樣式。|
|[put_BorderColor](#put_bordercolor)|呼叫這個方法來設定控制項的框線色彩。|
|[put_BorderStyle](#put_borderstyle)|呼叫這個方法來設定控制項的框線樣式。|
|[put_BorderVisible](#put_bordervisible)|呼叫這個方法來設定旗標的值，指出控制項的框線是否可見。|
|[put_BorderWidth](#put_borderwidth)|呼叫這個方法來設定控制項框線的寬度。|
|[put_Caption](#put_caption)|呼叫這個方法來設定要與控制項一起顯示的文字。|
|[put_DrawMode](#put_drawmode)|呼叫這個方法來設定控制項的繪圖模式，例如 XOR 畫筆或反相顏色。|
|[put_DrawStyle](#put_drawstyle)|呼叫這個方法來設定控制項的繪製樣式（例如，實線、虛線或點線）。|
|[put_DrawWidth](#put_drawwidth)|呼叫這個方法，以圖元為單位來設定控制項的繪圖方法所使用的寬度 (（以圖元) 為單位）。|
|[put_Enabled](#put_enabled)|呼叫這個方法來設定旗標，這個旗標會指出是否已啟用控制項。|
|[put_FillColor](#put_fillcolor)|呼叫這個方法來設定控制項的填滿色彩。|
|[put_FillStyle](#put_fillstyle)|呼叫這個方法來設定控制項的填滿樣式，例如，純色、透明或交叉影線。|
|[put_Font](#put_font)|呼叫這個方法來設定控制項的字型屬性。|
|[put_ForeColor](#put_forecolor)|呼叫這個方法來設定控制項的前景色彩。|
|[put_HWND](#put_hwnd)|這個方法會傳回 E_FAIL。|
|[put_MouseIcon](#put_mouseicon)|呼叫這個方法來設定圖形 (圖示、點陣圖或中繼檔的圖片屬性) 在滑鼠停留在控制項上時顯示。|
|[put_MousePointer](#put_mousepointer)|當滑鼠停留在控制項上時，呼叫這個方法來設定顯示的滑鼠指標類型，例如箭號、交叉或沙漏。|
|[put_Picture](#put_picture)|呼叫這個方法來設定要顯示之圖形 (圖示、點陣圖或中繼檔) 的圖片屬性。|
|[put_ReadyState](#put_readystate)|呼叫這個方法來設定控制項的就緒狀態，例如載入或載入。|
|[put_TabStop](#put_tabstop)|呼叫這個方法來設定旗標的值，這個值表示控制項是否為 tab 鍵停用。|
|[put_Text](#put_text)|呼叫這個方法來設定與控制項一起顯示的文字。|
|[putvalid](#put_valid)|呼叫這個方法來設定旗標，以指出控制項是否有效。|
|[put_Window](#put_window)|這個方法會呼叫 [CStockPropImpl：:p ut_HWND](#put_hwnd)，它會傳回 E_FAIL。|
|[putref_Font](#putref_font)|呼叫這個方法來設定控制項的字型屬性，以及參考計數。|
|[putref_MouseIcon](#putref_mouseicon)|呼叫這個方法來設定圖形 (圖示、點陣圖或中繼檔的圖片屬性，) 在滑鼠停留在控制項上時顯示，而且具有參考計數。|
|[putref_Picture](#putref_picture)|呼叫這個方法，即可使用參考計數來設定要顯示之圖形 (圖示、點陣圖或中繼檔) 的圖片屬性。|

## <a name="remarks"></a>備註

`CStockPropImpl` 為每個內建屬性提供 **put** 和 **get** 方法。 這些方法會提供設定或取得與每個屬性相關聯的資料成員所需的程式碼，以及在任何屬性變更時通知並與容器進行同步處理。

Visual Studio 透過其嚮導提供內建屬性的支援。 如需將內建屬性加入至控制項的詳細資訊，請參閱 [ATL 教學](../../atl/active-template-library-atl-tutorial.md)課程。

為了回溯相容性， `CStockPropImpl` 也 `get_Window` `put_Window` 會公開簡單的和方法，分別呼叫 `get_HWND` 和 `put_HWND` 。 的預設執行 `put_HWND` 會傳回 E_FAIL，因為 HWND 應為唯讀屬性。

下列屬性也有 **putref** 的執行：

- 字型

- MouseIcon

- Picture

相同的三個內建屬性需要其對應的資料成員屬於類型 `CComPtr` 或其他類別，以透過指派運算子提供正確的介面參考計數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>規格需求

**標頭：** atlctl。h

## <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a> CStockPropImpl：： get_Appearance

呼叫這個方法以取得控制項所使用的繪製樣式，例如，平面或3D。

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>參數

*pnAppearance*<br/>
接收控制項油漆樣式的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a> CStockPropImpl：： get_AutoSize

呼叫這個方法，以取得指出控制項是否不能是任何其他大小的旗標狀態。

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>參數

*pbAutoSize*<br/>
接收旗標狀態的變數。 TRUE 表示控制項不能是任何其他大小。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a> CStockPropImpl：： get_BackColor

呼叫這個方法來取得控制項的背景色彩。

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>參數

*pclrBackColor*<br/>
此變數會接收控制項的背景色彩。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a> CStockPropImpl：： get_BackStyle

呼叫這個方法來取得控制項的背景樣式，也就是透明或不透明。

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>參數

*pnBackStyle*<br/>
接收控制項背景樣式的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a> CStockPropImpl：： get_BorderColor

呼叫這個方法來取得控制項的框線色彩。

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>參數

*pclrBorderColor*<br/>
接收控制項框線色彩的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a> CStockPropImpl：： get_BorderStyle

呼叫這個方法來取得控制項的框線樣式。

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>參數

*pnBorderStyle*<br/>
接收控制項框線樣式的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a> CStockPropImpl：： get_BorderVisible

呼叫這個方法，以取得指出控制項框線是否可見的旗標狀態。

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>參數

*pbBorderVisible*<br/>
接收旗標狀態的變數。 TRUE 表示可以看到控制項的框線。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a> CStockPropImpl：： get_BorderWidth

呼叫這個方法以取得控制項框線的寬度。

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>參數

*pnBorderWidth*<br/>
接收控制項框線寬度的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_caption"></a><a name="get_caption"></a> CStockPropImpl：： get_Caption

呼叫這個方法，以取得物件標題中指定的文字。

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>參數

*pbstrCaption*<br/>
要與控制項一起顯示的文字。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a> CStockPropImpl：： get_DrawMode

呼叫這個方法來取得控制項的繪圖模式，例如 XOR 畫筆或反相顏色。

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>參數

*pnDrawMode*<br/>
接收控制項繪圖模式的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a> CStockPropImpl：： get_DrawStyle

呼叫這個方法來取得控制項的繪製樣式，例如，實線、虛線或點線。

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>參數

*pnDrawStyle*<br/>
接收控制項繪製樣式的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a> CStockPropImpl：： get_DrawWidth

呼叫這個方法可取得控制項的繪圖方法所使用的繪圖寬度 (（以圖元為單位）) 。

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>參數

*pnDrawWidth*<br/>
接收控制項寬度值的變數（以圖元為單位）。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a> CStockPropImpl：： get_Enabled

呼叫這個方法，以取得指出是否已啟用控制項的旗標狀態。

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>參數

*pbEnabled*<br/>
接收旗標狀態的變數。 TRUE 表示已啟用控制項。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a> CStockPropImpl：： get_FillColor

呼叫這個方法來取得控制項的填滿色彩。

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>參數

*pclrFillColor*<br/>
接收控制項填滿色彩的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a> CStockPropImpl：： get_FillStyle

呼叫這個方法來取得控制項的填滿樣式，例如，純色、透明或 crosshatched。

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>參數

*pnFillStyle*<br/>
接收控制項填滿樣式的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_font"></a><a name="get_font"></a> CStockPropImpl：： get_Font

呼叫這個方法，以取得控制項字型屬性的指標。

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>參數

*ppFont*<br/>
接收控制項字型屬性指標的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a> CStockPropImpl：： get_ForeColor

呼叫這個方法來取得控制項的前景色彩。

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>參數

*pclrForeColor*<br/>
接收控制項前景色彩的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a> CStockPropImpl：： get_HWND

呼叫這個方法，以取得與控制項相關聯的視窗控制碼。

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>參數

*phWnd*<br/>
與控制項相關聯的視窗控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a> CStockPropImpl：： get_MouseIcon

呼叫這個方法，取得圖形 (圖示、點陣圖或中繼檔的圖片屬性) 在滑鼠停留在控制項上時顯示。

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>參數

*ppPicture*<br/>
接收圖形圖片屬性指標的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a> CStockPropImpl：： get_MousePointer

呼叫這個方法，以取得滑鼠停留在控制項上時所顯示的滑鼠指標類型，例如箭號、交叉或沙漏。

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>參數

*pnMousePointer*<br/>
接收滑鼠指標類型的變數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_picture"></a><a name="get_picture"></a> CStockPropImpl：： get_Picture

呼叫這個方法，取得圖形 (圖示、點陣圖或中繼檔的圖片屬性指標，) 要顯示的內容。

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>參數

*ppPicture*<br/>
接收圖片屬性指標的變數。 如需詳細資訊，請參閱 [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a> CStockPropImpl：： get_ReadyState

呼叫這個方法以取得控制項的就緒狀態，例如載入或載入。

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>參數

*pnReadyState*<br/>
此變數會接收控制項的就緒狀態。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a> CStockPropImpl：： get_TabStop

呼叫這個方法來取得旗標的狀態，指出控制項是否為 tab 鍵停用。

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>參數

*pbTabStop*<br/>
接收旗標狀態的變數。 TRUE 表示控制項是定位停駐點。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_text"></a><a name="get_text"></a> CStockPropImpl：： get_Text

呼叫這個方法來取得與控制項一起顯示的文字。

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>參數

*pbstrText*<br/>
與控制項一起顯示的文字。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a> CStockPropImpl：： getvalid

呼叫這個方法，以取得指出控制項是否有效的旗標狀態。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>參數

*pbValid*<br/>
接收旗標狀態的變數。 TRUE 表示控制項有效。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplget_window"></a><a name="get_window"></a> CStockPropImpl：： get_Window

呼叫這個方法，以取得與控制項相關聯的視窗控制碼。 與 [CStockPropImpl：： get_HWND](#get_hwnd)相同。

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>參數

*phWnd*<br/>
與控制項相關聯的視窗控制碼。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a> CStockPropImpl：:p ut_Appearance

呼叫這個方法來設定控制項所使用的繪製樣式，例如，平面或3D。

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>參數

*nAppearance*<br/>
控制項要使用的新繪製樣式。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a> CStockPropImpl：:p ut_AutoSize

呼叫這個方法來設定旗標的值，這個值會指出控制項是否不能是任何其他大小。

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>參數

*bAutoSize*<br/>
如果控制項不能是任何其他大小，則為 TRUE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a> CStockPropImpl：:p ut_BackColor

呼叫這個方法來設定控制項的背景色彩。

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>參數

*clrBackColor*<br/>
新的控制項背景色彩。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a> CStockPropImpl：:p ut_BackStyle

呼叫這個方法來設定控制項的背景樣式。

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>參數

*nBackStyle*<br/>
新的控制項背景樣式。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a> CStockPropImpl：:p ut_BorderColor

呼叫這個方法來設定控制項的框線色彩。

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>參數

*clrBorderColor*<br/>
新的框線色彩。 OLE_COLOR 資料類型在內部表示為32位長整數。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a> CStockPropImpl：:p ut_BorderStyle

呼叫這個方法來設定控制項的框線樣式。

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>參數

*nBorderStyle*<br/>
新的框線樣式。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a> CStockPropImpl：:p ut_BorderVisible

呼叫這個方法來設定旗標的值，指出控制項的框線是否可見。

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>參數

*bBorderVisible*<br/>
如果框線是可見的，則為 TRUE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a> CStockPropImpl：:p ut_BorderWidth

呼叫這個方法來設定控制項框線的寬度。

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>參數

*nBorderWidth*<br/>
控制項框線的新寬度。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_caption"></a><a name="put_caption"></a> CStockPropImpl：:p ut_Caption

呼叫這個方法來設定要與控制項一起顯示的文字。

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>參數

*bstrCaption*<br/>
要與控制項一起顯示的文字。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a> CStockPropImpl：:p ut_DrawMode

呼叫這個方法來設定控制項的繪圖模式，例如 XOR 畫筆或反相顏色。

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>參數

*nDrawMode*<br/>
控制項的新繪圖模式。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a> CStockPropImpl：:p ut_DrawStyle

呼叫這個方法來設定控制項的繪製樣式（例如，實線、虛線或點線）。

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>參數

*nDrawStyle*<br/>
控制項的新繪製樣式。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a> CStockPropImpl：:p ut_DrawWidth

呼叫這個方法，以圖元為單位來設定控制項的繪圖方法所使用的寬度 (（以圖元) 為單位）。

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>參數

*nDrawWidth*<br/>
控制項繪圖方法所要使用的新寬度。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a> CStockPropImpl：:p ut_Enabled

呼叫這個方法來設定旗標的值，這個值會指出是否已啟用控制項。

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>參數

*bEnabled*<br/>
如果已啟用控制項，則為 TRUE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a> CStockPropImpl：:p ut_FillColor

呼叫這個方法來設定控制項的填滿色彩。

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>參數

*clrFillColor*<br/>
控制項的新填滿色彩。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a> CStockPropImpl：:p ut_FillStyle

呼叫這個方法來設定控制項的填滿樣式，例如，純色、透明或交叉影線。

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>參數

*nFillStyle*<br/>
控制項的新填滿樣式。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_font"></a><a name="put_font"></a> CStockPropImpl：:p ut_Font

呼叫這個方法來設定控制項的字型屬性。

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
控制項字型屬性的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a> CStockPropImpl：:p ut_ForeColor

呼叫這個方法來設定控制項的前景色彩。

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>參數

*clrForeColor*<br/>
控制項的新前景色彩。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a> CStockPropImpl：:p ut_HWND

這個方法會傳回 E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
保留的。

### <a name="return-value"></a>傳回值

傳回 E_FAIL。

### <a name="remarks"></a>備註

視窗控制碼是唯讀值。

## <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a> CStockPropImpl：:p ut_MouseIcon

呼叫這個方法來設定圖形 (圖示、點陣圖或中繼檔的圖片屬性) 在滑鼠停留在控制項上時顯示。

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*pPicture*<br/>
圖形的圖片屬性指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a> CStockPropImpl：:p ut_MousePointer

當滑鼠停留在控制項上時，呼叫這個方法來設定顯示的滑鼠指標類型，例如箭號、交叉或沙漏。

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>參數

*nMousePointer*<br/>
滑鼠指標的類型。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_picture"></a><a name="put_picture"></a> CStockPropImpl：:p ut_Picture

呼叫這個方法來設定要顯示之圖形 (圖示、點陣圖或中繼檔) 的圖片屬性。

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*pPicture*<br/>
圖片屬性的指標。 如需詳細資訊，請參閱 [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a> CStockPropImpl：:p ut_ReadyState

呼叫這個方法來設定控制項的就緒狀態，例如載入或載入。

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>參數

*nReadyState*<br/>
控制項的就緒狀態。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a> CStockPropImpl：:p ut_TabStop

呼叫這個方法來設定旗標，指出控制項是否為 tab 鍵停用。

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>參數

*bTabStop*<br/>
如果控制項是定位停駐點，則為 TRUE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_text"></a><a name="put_text"></a> CStockPropImpl：:p ut_Text

呼叫這個方法來設定與控制項一起顯示的文字。

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>參數

*bstrText*<br/>
與控制項一起顯示的文字。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplputvalid"></a><a name="put_valid"></a> CStockPropImpl：:p utvalid

呼叫這個方法來設定旗標，以指出控制項是否有效。

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>參數

*bValid*<br/>
如果控制項有效，則為 TRUE。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

## <a name="cstockpropimplput_window"></a><a name="put_window"></a> CStockPropImpl：:p ut_Window

這個方法會呼叫 [CStockPropImpl：:p ut_HWND](#put_hwnd)，它會傳回 E_FAIL。

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>參數

*hWnd*<br/>
視窗控制代碼 (Window Handle)。

### <a name="return-value"></a>傳回值

傳回 E_FAIL。

### <a name="remarks"></a>備註

視窗控制碼是唯讀值。

## <a name="cstockpropimplputref_font"></a><a name="putref_font"></a> CStockPropImpl：:p utref_Font

呼叫這個方法來設定控制項的字型屬性，以及參考計數。

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>參數

*pFont*<br/>
控制項字型屬性的指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

相同于 [CStockPropImpl：:p ut_Font](#put_font)，但是具有參考計數。

## <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a> CStockPropImpl：:p utref_MouseIcon

呼叫這個方法來設定圖形 (圖示、點陣圖或中繼檔的圖片屬性，) 在滑鼠停留在控制項上時顯示，而且具有參考計數。

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*pPicture*<br/>
圖形的圖片屬性指標。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

相同于 [CStockPropImpl：:p ut_MouseIcon](#put_mouseicon)，但是具有參考計數。

## <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a> CStockPropImpl：:p utref_Picture

呼叫這個方法，即可使用參考計數來設定要顯示之圖形 (圖示、點陣圖或中繼檔) 的圖片屬性。

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>參數

*pPicture*<br/>
圖片屬性的指標。 如需詳細資訊，請參閱 [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK，或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

相同于 [CStockPropImpl：:p ut_Picture](#put_picture)，但是具有參考計數。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)
