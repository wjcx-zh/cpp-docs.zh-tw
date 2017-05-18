---
title: "CStockPropImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 366da264f62364a39f6dfe9903a1a19a89266d33
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cstockpropimpl-class"></a>CStockPropImpl 類別
這個類別提供支援的內建屬性值的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE CStockPropImpl : public IDispatchImpl<InterfaceName, piid,
 plibid,
    wMajor,
 wMinor,
    tihclass>
```   
  
#### <a name="parameters"></a>參數  
 `T`  
 實作控制項類別衍生自`CStockPropImpl`。  
  
 `InterfaceName`  
 雙重介面公開內建屬性。  
  
 `piid`  
 指標的 IID `InterfaceName`。  
  
 `plibid`  
 包含定義的型別程式庫的 LIBID 指標`InterfaceName`。  
  
 `wMajor`  
 型別程式庫的主要版本。 預設值為 1。  
  
 `wMinor`  
 次要類型程式庫版本。 預設值為 0。  
  
 `tihclass`  
 用來管理的型別資訊的類別`T`。 預設值是 `CComTypeInfoHolder`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|[get_Appearance](#get_appearance)|呼叫這個方法來取得繪製樣式控制項所使用，例如，一般或 3D。|  
|[get_AutoSize](#get_autosize)|呼叫這個方法來取得狀態的旗標，指出是否控制項不能是任何其他大小。|  
|[get_BackColor](#get_backcolor)|呼叫這個方法來取得控制項的背景色彩。|  
|[get_BackStyle](#get_backstyle)|呼叫這個方法來取得控制項的背景樣式、 透明或不透明。|  
|[get_BorderColor](#get_bordercolor)|呼叫這個方法來取得控制項的框線色彩。|  
|[get_BorderStyle](#get_borderstyle)|呼叫這個方法來取得控制項的框線樣式。|  
|[get_BorderVisible](#get_bordervisible)|呼叫這個方法來取得狀態的旗標，指出控制項的框線是否為可見。|  
|[get_BorderWidth](#get_borderwidth)|呼叫這個方法來取得控制項的框線的寬度 （以像素為單位）。|  
|[get_Caption](#get_caption)|呼叫這個方法，取得指定物件的標題中的文字。|  
|[get_DrawMode](#get_drawmode)|呼叫這個方法來取得控制項的繪圖模式，例如 XOR 畫筆或色彩對換。|  
|[get_DrawStyle](#get_drawstyle)|呼叫這個方法來取得控制項的繪製樣式，例如，實線、 虛線或點線。|  
|[get_DrawWidth](#get_drawwidth)|呼叫這個方法來取得控制項的繪圖方法所使用的繪圖寬度 （以像素為單位）。|  
|[get_Enabled](#get_enabled)|呼叫這個方法來取得旗標，指出是否啟用控制項的狀態。|  
|[get_FillColor](#get_fillcolor)|呼叫這個方法來取得控制項的填滿色彩。|  
|[get_FillStyle](#get_fillstyle)|呼叫這個方法來取得控制項的填滿樣式，比方說，實線、 透明的或斜線。|  
|[get_Font](#get_font)|呼叫這個方法來取得控制項的字型屬性的指標。|  
|[get_ForeColor](#get_forecolor)|呼叫這個方法來取得控制項的前景色彩。|  
|[get_HWND](#get_hwnd)|呼叫這個方法來取得與控制項關聯的視窗控制代碼。|  
|[get_MouseIcon](#get_mouseicon)|呼叫這個方法來取得圖形 （圖示、 點陣圖或中繼檔） 滑鼠位於控制項上方時所要顯示的圖片屬性。|  
|[get_MousePointer](#get_mousepointer)|呼叫這個方法來取得滑鼠指標時，顯示滑鼠移至控制項，例如，箭號、 跨或沙漏的型別。|  
|[get_Picture](#get_picture)|呼叫這個方法來取得圖片 （圖示、 點陣圖或中繼檔） 會顯示圖片內容的指標。|  
|[get_ReadyState](#get_readystate)|呼叫這個方法來取得控制項的就緒狀態，例如，載入或載入。|  
|[get_TabStop](#get_tabstop)|呼叫這個方法來取得旗標，指出控制項是否定位停駐點。|  
|[get_Text](#get_text)|呼叫這個方法，以取得與控制項所顯示的文字。|  
|[getvalid](#get_valid)|呼叫這個方法來取得旗標，指出控制項是否為有效的狀態。|  
|[get_Window](#get_window)|呼叫這個方法來取得與控制項關聯的視窗控制代碼。 等於[CStockPropImpl::get_HWND](#get_hwnd)。|  
|[put_Appearance](#put_appearance)|呼叫這個方法來設定 [小畫家] 樣式控制項所使用，例如，一般或 3D。|  
|[put_AutoSize](#put_autosize)|呼叫這個方法來設定旗標，指出是否控制項不能是任何其他大小的值。|  
|[put_BackColor](#put_backcolor)|呼叫這個方法來設定控制項的背景色彩。|  
|[put_BackStyle](#put_backstyle)|呼叫這個方法來設定控制項的背景樣式。|  
|[put_BorderColor](#put_bordercolor)|呼叫這個方法來設定控制項的框線色彩。|  
|[put_BorderStyle](#put_borderstyle)|呼叫這個方法以設定控制項的框線樣式。|  
|[put_BorderVisible](#put_bordervisible)|呼叫這個方法來設定旗標，指出控制項的框線是否為可見的值。|  
|[put_BorderWidth](#put_borderwidth)|呼叫這個方法來設定控制項的框線寬度。|  
|[put_Caption](#put_caption)|呼叫這個方法來設定要顯示與控制項的文字。|  
|[put_DrawMode](#put_drawmode)|呼叫這個方法來設定控制項的繪製模式，例如 XOR 畫筆或色彩對換。|  
|[put_DrawStyle](#put_drawstyle)|呼叫這個方法，以設定控制項的繪製樣式，例如，實線、 虛線或點線。|  
|[put_DrawWidth](#put_drawwidth)|呼叫這個方法來設定控制項的繪圖方法所使用的寬度 （以像素為單位）。|  
|[put_Enabled](#put_enabled)|呼叫這個方法來設定旗標，指出是否啟用控制項。|  
|[put_FillColor](#put_fillcolor)|呼叫這個方法來設定控制項的填滿色彩。|  
|[put_FillStyle](#put_fillstyle)|呼叫這個方法，以設定控制項的填滿樣式，比方說，實線、 透明的或斜線。|  
|[put_Font](#put_font)|呼叫這個方法來設定控制項的字型屬性。|  
|[put_ForeColor](#put_forecolor)|呼叫這個方法來設定控制項的前景色彩。|  
|[put_HWND](#put_hwnd)|這個方法會傳回 E_FAIL。|  
|[put_MouseIcon](#put_mouseicon)|呼叫此方法以設定圖形 （圖示、 點陣圖或中繼檔） 滑鼠位於控制項上方時所要顯示的圖片屬性。|  
|[put_MousePointer](#put_mousepointer)|呼叫這個方法來設定顯示滑鼠經過控制項，例如當滑鼠指標、 箭號、 跨或沙漏的類型。|  
|[put_Picture](#put_picture)|呼叫此方法以設定圖形 （圖示、 點陣圖或中繼檔） 要顯示的圖片屬性。|  
|[put_ReadyState](#put_readystate)|呼叫這個方法，以設定控制項的就緒狀態，例如，載入或載入。|  
|[put_TabStop](#put_tabstop)|呼叫這個方法來設定旗標，指出控制項是否定位停駐點的值。|  
|[put_Text](#put_text)|呼叫這個方法來設定與控制項所顯示的文字。|  
|[putvalid](#put_valid)|呼叫這個方法來設定旗標，指出控制項是否為有效。|  
|[put_Window](#put_window)|這個方法會呼叫[CStockPropImpl::put_HWND](#put_hwnd)，它會傳回 E_FAIL。|  
|[putref_Font](#putref_font)|呼叫這個方法來設定控制項的字型屬性，參考計數。|  
|[putref_MouseIcon](#putref_mouseicon)|呼叫這個方法，以設定圖形 （圖示、 點陣圖或中繼檔） 滑鼠經過控制項時所要顯示的圖片屬性的參考計數。|  
|[putref_Picture](#putref_picture)|呼叫這個方法，以設定圖形 （圖示、 點陣圖或中繼檔） 要顯示的圖片屬性的參考計數。|  
  
## <a name="remarks"></a>備註  
 `CStockPropImpl`提供**放**和**取得**每個內建屬性的方法。 這些方法會提供所需程式碼來設定或取得每個屬性相關聯的資料成員和通知，並同步處理與容器的任何屬性變更時。  
  
 Visual c + + 內建屬性，透過其精靈提供支援。 如需內建屬性加入至控制項的詳細資訊，請參閱[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。  
  
 回溯相容性，`CStockPropImpl`也會公開`get_Window`和`put_Window`方法，只要呼叫`get_HWND`和`put_HWND`分別。 預設實作`put_HWND`傳回**E_FAIL**因為`HWND`應該是唯讀屬性。  
  
 下列屬性也有**putref**實作︰  
  
-   字型  
  
-   MouseIcon  
  
-   圖片  
  
 相同的三個內建屬性需要其對應的資料成員型別`CComPtr`或其他類別，提供正確的介面參考計數，透過指派運算子。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="get_appearance"></a>CStockPropImpl::get_Appearance  
 呼叫這個方法來取得繪製樣式控制項所使用，例如，一般或 3D。  
  
```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```  
  
### <a name="parameters"></a>參數  
 *pnAppearance*  
 變數會接收控制項的繪製樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_autosize"></a>CStockPropImpl::get_AutoSize  
 呼叫這個方法來取得狀態的旗標，指出是否控制項不能是任何其他大小。  
  
```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```  
  
### <a name="parameters"></a>參數  
 *pbAutoSize*  
 變數會接收旗標狀態。 TRUE 表示控制項不能是任何其他的大小。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_backcolor"></a>CStockPropImpl::get_BackColor  
 呼叫這個方法來取得控制項的背景色彩。  
  
```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```  
  
### <a name="parameters"></a>參數  
 *pclrBackColor*  
 變數會接收控制項的背景色彩。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_backstyle"></a>CStockPropImpl::get_BackStyle  
 呼叫這個方法來取得控制項的背景樣式、 透明或不透明。  
  
```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```  
  
### <a name="parameters"></a>參數  
 *pnBackStyle*  
 變數會接收控制項的背景樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_bordercolor"></a>CStockPropImpl::get_BorderColor  
 呼叫這個方法來取得控制項的框線色彩。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```  
  
### <a name="parameters"></a>參數  
 *pclrBorderColor*  
 變數會接收控制項的框線色彩。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_borderstyle"></a>CStockPropImpl::get_BorderStyle  
 呼叫這個方法來取得控制項的框線樣式。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```  
  
### <a name="parameters"></a>參數  
 *pnBorderStyle*  
 變數會接收控制項的框線樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_bordervisible"></a>CStockPropImpl::get_BorderVisible  
 呼叫這個方法來取得狀態的旗標，指出控制項的框線是否為可見。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```  
  
### <a name="parameters"></a>參數  
 *pbBorderVisible*  
 變數會接收旗標狀態。 TRUE 表示控制項的框線可見。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_borderwidth"></a>CStockPropImpl::get_BorderWidth  
 呼叫這個方法來取得控制項的框線寬度。  
  
```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```  
  
### <a name="parameters"></a>參數  
 *pnBorderWidth*  
 變數會接收控制項的框線寬度。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_caption"></a>CStockPropImpl::get_Caption  
 呼叫這個方法，取得指定物件的標題中的文字。  
  
```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```  
  
### <a name="parameters"></a>參數  
 *pbstrCaption*  
 若要使用控制項來顯示文字。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_drawmode"></a>CStockPropImpl::get_DrawMode  
 呼叫這個方法來取得控制項的繪圖模式，例如 XOR 畫筆或色彩對換。  
  
```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```  
  
### <a name="parameters"></a>參數  
 *pnDrawMode*  
 變數會接收控制項的繪圖模式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_drawstyle"></a>CStockPropImpl::get_DrawStyle  
 呼叫這個方法來取得控制項的繪製樣式，例如，實線、 虛線或點線。  
  
```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```  
  
### <a name="parameters"></a>參數  
 *pnDrawStyle*  
 變數會接收控制項的繪製樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_drawwidth"></a>CStockPropImpl::get_DrawWidth  
 呼叫這個方法來取得控制項的繪圖方法所使用的繪圖寬度 （以像素為單位）。  
  
```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```  
  
### <a name="parameters"></a>參數  
 *pnDrawWidth*  
 接收控制項的寬度值，單位為像素的變數。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_enabled"></a>CStockPropImpl::get_Enabled  
 呼叫這個方法來取得旗標，指出是否啟用控制項的狀態。  
  
```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```  
  
### <a name="parameters"></a>參數  
 `pbEnabled`  
 變數會接收旗標狀態。 TRUE 表示已啟用控制項。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_fillcolor"></a>CStockPropImpl::get_FillColor  
 呼叫這個方法來取得控制項的填滿色彩。  
  
```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```  
  
### <a name="parameters"></a>參數  
 *pclrFillColor*  
 變數會接收控制項的填滿色彩。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_fillstyle"></a>CStockPropImpl::get_FillStyle  
 呼叫這個方法來取得控制項的填滿樣式，比方說，穩固、 透明的或 crosshatched。  
  
```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```  
  
### <a name="parameters"></a>參數  
 *pnFillStyle*  
 接收控制項的填滿樣式的變數。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_font"></a>CStockPropImpl::get_Font  
 呼叫這個方法來取得控制項的字型屬性的指標。  
  
```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```  
  
### <a name="parameters"></a>參數  
 `ppFont`  
 接收控制項的字型屬性指向的變數。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_forecolor"></a>CStockPropImpl::get_ForeColor  
 呼叫這個方法來取得控制項的前景色彩。  
  
```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```  
  
### <a name="parameters"></a>參數  
 *pclrForeColor*  
 變數會接收控制項的前景色彩。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_hwnd"></a>CStockPropImpl::get_HWND  
 呼叫這個方法來取得與控制項關聯的視窗控制代碼。  
  
```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>參數  
 `phWnd`  
 與控制項關聯的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_mouseicon"></a>CStockPropImpl::get_MouseIcon  
 呼叫這個方法來取得圖形 （圖示、 點陣圖或中繼檔） 滑鼠位於控制項上方時所要顯示的圖片屬性。  
  
```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>參數  
 `ppPicture`  
 變數會接收圖形的圖片內容的指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_mousepointer"></a>CStockPropImpl::get_MousePointer  
 呼叫這個方法來取得滑鼠指標時，顯示滑鼠移至控制項，例如，箭號、 跨或沙漏的型別。  
  
```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```  
  
### <a name="parameters"></a>參數  
 *pnMousePointer*  
 變數會接收滑鼠指標的類型。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_picture"></a>CStockPropImpl::get_Picture  
 呼叫這個方法來取得圖片 （圖示、 點陣圖或中繼檔） 會顯示圖片內容的指標。  
  
```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```  
  
### <a name="parameters"></a>參數  
 `ppPicture`  
 變數會接收圖片內容的指標。 請參閱[IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_readystate"></a>CStockPropImpl::get_ReadyState  
 呼叫這個方法來取得控制項的就緒狀態，例如，載入或載入。  
  
```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```  
  
### <a name="parameters"></a>參數  
 *pnReadyState*  
 接收控制項的就緒狀態的變數。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_tabstop"></a>CStockPropImpl::get_TabStop  
 呼叫這個方法來取得狀態的旗標，指出控制項是否定位停駐點。  
  
```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```  
  
### <a name="parameters"></a>參數  
 *pbTabStop*  
 變數會接收旗標狀態。 TRUE 表示此控制項是一個定位點。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_text"></a>CStockPropImpl::get_Text  
 呼叫這個方法，以取得與控制項所顯示的文字。  
  
```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```  
  
### <a name="parameters"></a>參數  
 *pbstrText*  
 顯示與控制項的文字。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_valid"></a>CStockPropImpl::getvalid  
 呼叫這個方法來取得旗標，指出控制項是否為有效的狀態。  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```  
  
### <a name="parameters"></a>參數  
 *pbValid*  
 變數會接收旗標狀態。 TRUE 表示控制項有效。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="get_window"></a>CStockPropImpl::get_Window  
 呼叫這個方法來取得與控制項關聯的視窗控制代碼。 等於[CStockPropImpl::get_HWND](#get_hwnd)。  
  
```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```  
  
### <a name="parameters"></a>參數  
 `phWnd`  
 與控制項關聯的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_appearance"></a>CStockPropImpl::put_Appearance  
 呼叫這個方法來設定 [小畫家] 樣式控制項所使用，例如，一般或 3D。  
  
```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```  
  
### <a name="parameters"></a>參數  
 `nAppearance`  
 控制項可供新的繪製樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_autosize"></a>CStockPropImpl::put_AutoSize  
 呼叫這個方法來設定旗標，指出是否控制項不能是任何其他大小的值。  
  
```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```  
  
### <a name="parameters"></a>參數  
 *bAutoSize*  
 如果控制項不能是任何其他大小，則為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_backcolor"></a>CStockPropImpl::put_BackColor  
 呼叫這個方法來設定控制項的背景色彩。  
  
```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```  
  
### <a name="parameters"></a>參數  
 *clrBackColor*  
 新控制項的背景色彩。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_backstyle"></a>CStockPropImpl::put_BackStyle  
 呼叫這個方法來設定控制項的背景樣式。  
  
```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```  
  
### <a name="parameters"></a>參數  
 *nBackStyle*  
 新的控制項背景樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_bordercolor"></a>CStockPropImpl::put_BorderColor  
 呼叫這個方法來設定控制項的框線色彩。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```  
  
### <a name="parameters"></a>參數  
 *clrBorderColor*  
 新的框線色彩。 OLE_COLOR 資料型別是在內部表示為 32 位元長整數。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_borderstyle"></a>CStockPropImpl::put_BorderStyle  
 呼叫這個方法以設定控制項的框線樣式。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```  
  
### <a name="parameters"></a>參數  
 *nBorderStyle*  
 新的框線樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_bordervisible"></a>CStockPropImpl::put_BorderVisible  
 呼叫這個方法來設定旗標，指出控制項的框線是否為可見的值。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```  
  
### <a name="parameters"></a>參數  
 *bBorderVisible*  
 如果是可見的框線，則為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_borderwidth"></a>CStockPropImpl::put_BorderWidth  
 呼叫這個方法來設定控制項的框線寬度。  
  
```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```  
  
### <a name="parameters"></a>參數  
 `nBorderWidth`  
 新控制項的框線寬度。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_caption"></a>CStockPropImpl::put_Caption  
 呼叫這個方法來設定要顯示與控制項的文字。  
  
```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```  
  
### <a name="parameters"></a>參數  
 *bstrCaption*  
 若要使用控制項來顯示文字。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_drawmode"></a>CStockPropImpl::put_DrawMode  
 呼叫這個方法來設定控制項的繪製模式，例如 XOR 畫筆或色彩對換。  
  
```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```  
  
### <a name="parameters"></a>參數  
 `nDrawMode`  
 控制項新的繪圖模式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_drawstyle"></a>CStockPropImpl::put_DrawStyle  
 呼叫這個方法，以設定控制項的繪製樣式，例如，實線、 虛線或點線。  
  
```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```  
  
### <a name="parameters"></a>參數  
 *nDrawStyle*  
 控制項新的繪製樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_drawwidth"></a>CStockPropImpl::put_DrawWidth  
 呼叫這個方法來設定控制項的繪圖方法所使用的寬度 （以像素為單位）。  
  
```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```  
  
### <a name="parameters"></a>參數  
 *nDrawWidth*  
 控制項所使用的新寬度的繪圖方法。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_enabled"></a>CStockPropImpl::put_Enabled  
 呼叫這個方法來設定旗標，指出是否啟用控制項的值。  
  
```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```  
  
### <a name="parameters"></a>參數  
 `bEnabled`  
 如果控制項已啟用，則為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_fillcolor"></a>CStockPropImpl::put_FillColor  
 呼叫這個方法來設定控制項的填滿色彩。  
  
```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```  
  
### <a name="parameters"></a>參數  
 *clrFillColor*  
 控制項新的填滿色彩。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_fillstyle"></a>CStockPropImpl::put_FillStyle  
 呼叫這個方法，以設定控制項的填滿樣式，比方說，實線、 透明的或斜線。  
  
```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```  
  
### <a name="parameters"></a>參數  
 *nFillStyle*  
 控制項新的填滿樣式。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_font"></a>CStockPropImpl::put_Font  
 呼叫這個方法來設定控制項的字型屬性。  
  
```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>參數  
 `pFont`  
 指向控制項的字型屬性。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_forecolor"></a>CStockPropImpl::put_ForeColor  
 呼叫這個方法來設定控制項的前景色彩。  
  
```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```  
  
### <a name="parameters"></a>參數  
 *clrForeColor*  
 新的前景色彩的控制項。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_hwnd"></a>CStockPropImpl::put_HWND  
 這個方法會傳回 E_FAIL。  
  
```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```  
  
### <a name="parameters"></a>參數  
 */\*hWnd\*/*  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 傳回 E_FAIL。  
  
### <a name="remarks"></a>備註  
 視窗控制代碼是唯讀的值。  
  
##  <a name="put_mouseicon"></a>CStockPropImpl::put_MouseIcon  
 呼叫此方法以設定圖形 （圖示、 點陣圖或中繼檔） 滑鼠位於控制項上方時所要顯示的圖片屬性。  
  
```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>參數  
 `pPicture`  
 圖片圖片內容指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_mousepointer"></a>CStockPropImpl::put_MousePointer  
 呼叫這個方法來設定顯示滑鼠經過控制項，例如當滑鼠指標、 箭號、 跨或沙漏的類型。  
  
```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```  
  
### <a name="parameters"></a>參數  
 *nMousePointer*  
 滑鼠指標的類型。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_picture"></a>CStockPropImpl::put_Picture  
 呼叫此方法以設定圖形 （圖示、 點陣圖或中繼檔） 要顯示的圖片屬性。  
  
```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>參數  
 `pPicture`  
 圖片的內容指標。 請參閱[IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_readystate"></a>CStockPropImpl::put_ReadyState  
 呼叫這個方法，以設定控制項的就緒狀態，例如，載入或載入。  
  
```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```  
  
### <a name="parameters"></a>參數  
 *nReadyState*  
 控制項的就緒狀態。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_tabstop"></a>CStockPropImpl::put_TabStop  
 呼叫這個方法來設定旗標，指出控制項是否定位停駐點。  
  
```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```  
  
### <a name="parameters"></a>參數  
 *bTabStop*  
 如果控制項是定位停駐點，則為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_text"></a>CStockPropImpl::put_Text  
 呼叫這個方法來設定與控制項所顯示的文字。  
  
```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```  
  
### <a name="parameters"></a>參數  
 `bstrText`  
 顯示與控制項的文字。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_valid"></a>CStockPropImpl::putvalid  
 呼叫這個方法來設定旗標，指出控制項是否為有效。  
  
```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```  
  
### <a name="parameters"></a>參數  
 *bValid*  
 如果控制項為有效，則為 TRUE。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="put_window"></a>CStockPropImpl::put_Window  
 這個方法會呼叫[CStockPropImpl::put_HWND](#put_hwnd)，它會傳回 E_FAIL。  
  
```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 視窗控制代碼 (Window Handle)。  
  
### <a name="return-value"></a>傳回值  
 傳回 E_FAIL。  
  
### <a name="remarks"></a>備註  
 視窗控制代碼是唯讀的值。  
  
##  <a name="putref_font"></a>CStockPropImpl::putref_Font  
 呼叫這個方法來設定控制項的字型屬性，參考計數。  
  
```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```  
  
### <a name="parameters"></a>參數  
 `pFont`  
 指向控制項的字型屬性。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 相同[CStockPropImpl::put_Font](#put_font)，但是參考次數。  
  
##  <a name="putref_mouseicon"></a>CStockPropImpl::putref_MouseIcon  
 呼叫這個方法，以設定圖形 （圖示、 點陣圖或中繼檔） 滑鼠經過控制項時所要顯示的圖片屬性的參考計數。  
  
```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>參數  
 `pPicture`  
 圖片圖片內容指標。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 相同[CStockPropImpl::put_MouseIcon](#put_mouseicon)，但是參考次數。  
  
##  <a name="putref_picture"></a>CStockPropImpl::putref_Picture  
 呼叫這個方法，以設定圖形 （圖示、 點陣圖或中繼檔） 要顯示的圖片屬性的參考計數。  
  
```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```  
  
### <a name="parameters"></a>參數  
 `pPicture`  
 圖片的內容指標。 請參閱[IPictureDisp](http://msdn.microsoft.com/library/windows/desktop/ms680762)如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 相同[CStockPropImpl::put_Picture](#put_picture)，但是參考次數。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)   
 [IDispatchImpl 類別](../../atl/reference/idispatchimpl-class.md)

