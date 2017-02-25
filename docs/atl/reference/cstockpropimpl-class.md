---
title: "CStockPropImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStockPropImpl"
  - "ATL::CStockPropImpl"
  - "ATL.CStockPropImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控制項 [ATL], 內建屬性"
  - "CStockPropImpl class"
  - "內建屬性, ATL 控制項"
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CStockPropImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供對支援內建屬性值的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
class InterfaceName,   
const IID* piid= &_ATL_IIDOF(InterfaceName),   
const GUID* plibid= &CComModule::m_libid,   
WORD wMajor= 1,  
WORD wMinor= 0,   
class tihclass= CcomTypeInfoHolder  
>  
class ATL_NO_VTABLE CStockPropImpl :  
public IDispatchImpl< InterfaceName, piid, plibid, wMajor,  
   wMinor, tihclass>  
```  
  
#### 參數  
 `T`  
 實作控制項和 `CStockPropImpl`衍生自的類別。  
  
 `InterfaceName`  
 公開內建屬性的雙重介面。  
  
 `piid`  
 為 `InterfaceName`IID 的指標。  
  
 `plibid`  
 對型別包含 `InterfaceName`定義之程式庫的 GUID 的指標。  
  
 `wMajor`  
 型別程式庫的主要版本。  預設值為 1。  
  
 `wMinor`  
 型別程式庫的次要版本。  預設值為 0。  
  
 `tihclass`  
 所使用的類別處理 `T`的型別資訊。  預設值是 `CComTypeInfoHolder`。  
  
## Members  
  
### 公用方法  
  
|||  
|-|-|  
|[get\_Appearance](../Topic/CStockPropImpl::get_Appearance.md)|呼叫這個方法會取得繪製樣式使用控制項，例如，一般或 3D。|  
|[get\_AutoSize](../Topic/CStockPropImpl::get_AutoSize.md)|呼叫這個方法會取得表示旗標狀態的控制項不能是其他大小。|  
|[get\_BackColor](../Topic/CStockPropImpl::get_BackColor.md)|呼叫這個方法會取得控制項的背景色彩。|  
|[get\_BackStyle](../Topic/CStockPropImpl::get_BackStyle.md)|呼叫這個方法會取得控制項的背景樣式，透明或不透明。|  
|[get\_BorderColor](../Topic/CStockPropImpl::get_BorderColor.md)|呼叫這個方法會取得控制項的框線色彩。|  
|[get\_BorderStyle](../Topic/CStockPropImpl::get_BorderStyle.md)|呼叫這個方法會取得控制項的框線樣式。|  
|[get\_BorderVisible](../Topic/CStockPropImpl::get_BorderVisible.md)|呼叫這個方法會取得表示旗標狀態的控制項框線是否為可見。|  
|[get\_BorderWidth](../Topic/CStockPropImpl::get_BorderWidth.md)|呼叫這個方法會取得寬度 \(以像素為單位\) 的控制項的框線。|  
|[get\_Caption](../Topic/CStockPropImpl::get_Caption.md)|呼叫這個方法會取得指定物件中的文字標題。|  
|[get\_DrawMode](../Topic/CStockPropImpl::get_DrawMode.md)|呼叫這個方法會取得控制項的繪製模式，例如，位元 XOR 筆或反轉色彩。|  
|[get\_DrawStyle](../Topic/CStockPropImpl::get_DrawStyle.md)|呼叫這個方法會取得控制項的繪製模式，例如，實線，虛線則為多了。|  
|[get\_DrawWidth](../Topic/CStockPropImpl::get_DrawWidth.md)|呼叫這個方法會取得繪圖寬度 \(以像素為單位\) 使用控制項的繪圖方法。|  
|[get\_Enabled](../Topic/CStockPropImpl::get_Enabled.md)|呼叫這個方法會取得表示旗標狀態的控制項。|  
|[get\_FillColor](../Topic/CStockPropImpl::get_FillColor.md)|呼叫這個方法會取得控制項的填滿色彩。|  
|[get\_FillStyle](../Topic/CStockPropImpl::get_FillStyle.md)|呼叫這個方法會取得控制項的填滿模式，例如，實線，透明或跨平台的縮放繪製。|  
|[get\_Font](../Topic/CStockPropImpl::get_Font.md)|呼叫這個方法可以使用控制項的字型屬性。|  
|[get\_ForeColor](../Topic/CStockPropImpl::get_ForeColor.md)|呼叫這個方法會取得控制項的前景色彩。|  
|[get\_HWND](../Topic/CStockPropImpl::get_HWND.md)|呼叫這個方法會取得視窗控制代碼關聯的控制項。|  
|[get\_MouseIcon](../Topic/CStockPropImpl::get_MouseIcon.md)|呼叫這個方法會取得圖形 \(圖示、點陣圖、中繼檔圖片\) 的屬性時，就會顯示滑鼠指標在控制項中。|  
|[get\_MousePointer](../Topic/CStockPropImpl::get_MousePointer.md)|當滑鼠指標在控制項，例如，箭號、十字或沙漏時，呼叫這個方法會取得滑鼠指標的型別中。|  
|[get\_Picture](../Topic/CStockPropImpl::get_Picture.md)|呼叫這個方法取得指標圖形 \(圖示、點陣圖、中繼檔圖片\) 的屬性隨即顯示。|  
|[get\_ReadyState](../Topic/CStockPropImpl::get_ReadyState.md)|呼叫這個方法會取得控制項的就緒狀態，例如，載入或載入。|  
|[get\_TabStop](../Topic/CStockPropImpl::get_TabStop.md)|呼叫這個方法會取得值的旗標會控制是否是定位停駐點。|  
|[get\_Text](../Topic/CStockPropImpl::get_Text.md)|呼叫這個方法會取得顯示於控制項的文字。|  
|[get\_Valid](../Topic/CStockPropImpl::get_Valid.md)|呼叫這個方法會取得表示旗標狀態控制是否有效。|  
|[get\_Window](../Topic/CStockPropImpl::get_Window.md)|呼叫這個方法會取得視窗控制代碼關聯的控制項。  與 [CStockPropImpl::get\_HWND](../Topic/CStockPropImpl::get_HWND.md)。|  
|[put\_Appearance](../Topic/CStockPropImpl::put_Appearance.md)|呼叫這個方法會設定控制項，例如，一般或 3D 使用的繪製樣式。|  
|[put\_AutoSize](../Topic/CStockPropImpl::put_AutoSize.md)|呼叫這個方法會設定布林值旗標的值控制是否不可以是其他大小。|  
|[put\_BackColor](../Topic/CStockPropImpl::put_BackColor.md)|呼叫這個方法會設定控制項的背景色彩。|  
|[put\_BackStyle](../Topic/CStockPropImpl::put_BackStyle.md)|呼叫這個方法會設定控制項的背景樣式。|  
|[put\_BorderColor](../Topic/CStockPropImpl::put_BorderColor.md)|呼叫這個方法會設定控制項的框線色彩。|  
|[put\_BorderStyle](../Topic/CStockPropImpl::put_BorderStyle.md)|呼叫這個方法會設定控制項的框線樣式。|  
|[put\_BorderVisible](../Topic/CStockPropImpl::put_BorderVisible.md)|呼叫這個方法會設定布林值旗標的值表示控制項的框線是否為可見的。|  
|[put\_BorderWidth](../Topic/CStockPropImpl::put_BorderWidth.md)|呼叫這個方法會設定控制項的框線寬度。|  
|[put\_Caption](../Topic/CStockPropImpl::put_Caption.md)|呼叫這個方法會設定要顯示的文字和控制項。|  
|[put\_DrawMode](../Topic/CStockPropImpl::put_DrawMode.md)|呼叫這個方法會設定控制項的繪製模式，例如，位元 XOR 筆或反轉色彩。|  
|[put\_DrawStyle](../Topic/CStockPropImpl::put_DrawStyle.md)|呼叫這個方法會設定控制項的繪製模式，例如，實線，虛線則為多了。|  
|[put\_DrawWidth](../Topic/CStockPropImpl::put_DrawWidth.md)|呼叫這個方法會設定控制項的繪圖方法 \(以像素為單位\) 使用的寬度。|  
|[put\_Enabled](../Topic/CStockPropImpl::put_Enabled.md)|呼叫這個方法會設定旗標 \(指出控制項是否已啟用。|  
|[put\_FillColor](../Topic/CStockPropImpl::put_FillColor.md)|呼叫這個方法會設定控制項的填滿色彩。|  
|[put\_FillStyle](../Topic/CStockPropImpl::put_FillStyle.md)|呼叫這個方法會設定控制項的填滿模式，例如，實線，透明或跨平台的縮放繪製。|  
|[put\_Font](../Topic/CStockPropImpl::put_Font.md)|呼叫這個方法會設定控制項的字型屬性。|  
|[put\_ForeColor](../Topic/CStockPropImpl::put_ForeColor.md)|呼叫這個方法會設定控制項的前景色彩。|  
|[put\_HWND](../Topic/CStockPropImpl::put_HWND.md)|這個方法會傳回 E\_FAIL。|  
|[put\_MouseIcon](../Topic/CStockPropImpl::put_MouseIcon.md)|呼叫這個方法會設定 \(圖示、點陣圖、中繼檔\) 中要顯示的圖片屬性圖形，當滑鼠指標在控制項中。|  
|[put\_MousePointer](../Topic/CStockPropImpl::put_MousePointer.md)|當滑鼠指標在控制項，例如，箭號、十字或沙漏時，呼叫這個方法會設定顯示的滑鼠指標型別。|  
|[put\_Picture](../Topic/CStockPropImpl::put_Picture.md)|呼叫這個方法會設定 \(圖示、點陣圖、中繼檔\) 中要顯示的圖片屬性圖形。|  
|[put\_ReadyState](../Topic/CStockPropImpl::put_ReadyState.md)|呼叫這個方法會設定控制項的就緒狀態，例如，載入或載入。|  
|[put\_TabStop](../Topic/CStockPropImpl::put_TabStop.md)|呼叫這個方法會設定布林值旗標的值控制是否是定位停駐點。|  
|[put\_Text](../Topic/CStockPropImpl::put_Text.md)|呼叫這個方法會設定顯示於控制項的文字。|  
|[put\_Valid](../Topic/CStockPropImpl::put_Valid.md)|呼叫這個方法會設定旗標 \(指出控制項是否有效。|  
|[put\_Window](../Topic/CStockPropImpl::put_Window.md)|呼叫這個方法 [CStockPropImpl::put\_HWND](../Topic/CStockPropImpl::put_HWND.md)，傳回 E\_FAIL。|  
|[putref\_Font](../Topic/CStockPropImpl::putref_Font.md)|呼叫這個方法會設定控制項的字型屬性，以參考計數。|  
|[putref\_MouseIcon](../Topic/CStockPropImpl::putref_MouseIcon.md)|呼叫這個方法會設定要顯示的圖形 \(圖示、點陣圖、中繼檔圖片\) 的屬性，當滑鼠指標在控制項時，會使用參考計數。|  
|[putref\_Picture](../Topic/CStockPropImpl::putref_Picture.md)|呼叫這個方法會設定要顯示的圖形 \(圖示、點陣圖、中繼檔圖片\) 的屬性，以參考計數。|  
  
## 備註  
 `CStockPropImpl` 為每個內建屬性提供 **put** 和 **get** 方法。  在屬性變更時，這些方法所需的程式碼設定或取得資料成員與每個屬性和循環和同步處理與容器。  
  
 Visual C\+\+ 提供內建屬性支援透過它的精靈。  如需加入內建屬性的詳細資訊加入至控制項，請參閱 [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。  
  
 考量到回溯相容性， `CStockPropImpl` 分別也會公開 `get_Window` 和呼叫 `get_HWND` 和 `put_HWND`的 `put_Window` 方法。  因為 `HWND` 應該是唯讀屬性， `put_HWND` 的預設實作會傳回 **E\_FAIL** 。  
  
 下列屬性也具有 **putref** 實作:  
  
-   Font  
  
-   MouseIcon  
  
-   圖片  
  
 相同的三個內建屬性要求其對應的資料成員提供計數透過指派運算子右側介面參考的型別 `CComPtr` 或其他類別。  
  
## 繼承階層架構  
 `T`  
  
 [IDispatchImpl](../../atl/reference/idispatchimpl-class.md)  
  
 `CStockPropImpl`  
  
## 需求  
 **Header:** atlctl.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [IDispatchImpl Class](../../atl/reference/idispatchimpl-class.md)