---
title: "CMFCButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
dev_langs:
- C++
helpviewer_keywords:
- CMFCButton::CreateObject method
- CMFCButton::DrawItem method
- CMFCButton::PreTranslateMessage method
- CMFCButton constructor
- CMFCButton::OnDrawParentBackground method
- CMFCButton class
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
caps.latest.revision: 35
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
ms.openlocfilehash: 89cd722ac15a1d9ac6b6c815c837559e302f0e68
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbutton-class"></a>CMFCButton 類別
`CMFCButton`類別將功能加入至[CButton](../../mfc/reference/cbutton-class.md)類別，例如對齊按鈕文字、 結合按鈕文字和影像、 選取游標和指定工具提示。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCButton : public CButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCButton::CMFCButton`|預設建構函式。|  
|`CMFCButton::~CMFCButton`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCButton::CleanUp](#cleanup)|重設內部變數，並釋放已配置的資源，例如影像、 點陣圖和圖示。|  
|`CMFCButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCButton::DrawItem`|主控描繪按鈕的視覺外觀變更時，由架構呼叫。 (覆寫[CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem)。)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|指定是否要在大型的工具提示視窗或截斷的版小工具提示視窗中的文字顯示完整的工具提示文字。|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|指定按鈕文字的字型是相同的應用程式 功能表上的字型。|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|指定按鈕的框線樣式是否對應至目前的 Windows 佈景主題。|  
|`CMFCButton::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|傳回基礎的工具提示控制項的參考。|  
|[CMFCButton::IsAutoCheck](#isautocheck)|指出核取方塊或選項按鈕是否為自動的按鈕。|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|指出是否要將按鈕設定為自動重複模式。|  
|[CMFCButton::IsCheckBox](#ischeckbox)|表示按鈕是否為核取方塊按鈕。|  
|[CMFCButton::IsChecked](#ischecked)|指出是否要檢查目前的按鈕。|  
|[CMFCButton::IsHighlighted](#ishighlighted)|表示按鈕會反白顯示。|  
|[CMFCButton::IsPressed](#ispressed)|指出是否推入並反白顯示的按鈕。|  
|[CMFCButton::IsPushed](#ispushed)|指出是否按下按鈕。|  
|[CMFCButton::IsRadioButton](#isradiobutton)|指出按鈕是否為選項按鈕。|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|指出目前的 Windows 佈景主題是否對應按鈕的框線樣式。|  
|`CMFCButton::OnDrawParentBackground`|指定區域中繪製按鈕的父代的背景。 (覆寫[AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|將按鈕設定為自動重複模式。|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|設定已核取按鈕的影像。|  
|[CMFCButton::SetFaceColor](#setfacecolor)|設定按鈕文字的背景色彩。|  
|[CMFCButton::SetImage](#setimage)|設定按鈕的影像。|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|設定資料指標的影像。|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|設定游標的左手邊的影像。|  
|[CMFCButton::SetStdImage](#setstdimage)|使用`CMenuImages`物件來設定按鈕的影像。|  
|[CMFCButton::SetTextColor](#settextcolor)|設定未選取按鈕的按鈕文字的色彩。|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|設定已選取按鈕的按鈕文字的色彩。|  
|[CMFCButton::SetTooltip](#settooltip)|關聯按鈕的工具提示。|  
|[CMFCButton::SizeToContent](#sizetocontent)|調整大小，以包含其按鈕文字和影像的按鈕。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|若要繪製按鈕架構呼叫。|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|若要繪製按鈕的框線架構呼叫。|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|若要繪製焦點矩形按鈕架構呼叫。|  
|[CMFCButton::OnDrawText](#ondrawtext)|若要繪製按鈕文字架構呼叫。|  
|[CMFCButton::OnFillBackground](#onfillbackground)|若要繪製背景的按鈕文字架構呼叫。|  
|[CMFCButton::SelectFont](#selectfont)|擷取與指定之的裝置內容相關聯的字型。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|指出是否要繪製焦點矩形按鈕周圍。|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|指出是否要將游標停留時，反白顯示 BS_CHECKBOX 樣式 按鈕。|  
|[CMFCButton::m_bRightImage](#m_brightimage)|指出是否要在按鈕的右邊顯示影像。|  
|[CMFCButton::m_bTransparent](#m_btransparent)|指出是否為透明的按鈕。|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|指定按鈕文字的對齊方式。|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|指定的按鈕，例如無框線、 一般，分號平面或 3D 樣式。|  
  
## <a name="remarks"></a>備註  
 其他類型的按鈕衍生自`CMFCButton`類別，例如[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)類別，可支援超連結，而`CMFCColorButton`類別，可支援色彩選擇器對話方塊。  
  
 樣式`CMFCButton`物件可以是*3D*，*一般*，*分號一般*或*無框線*。 可以在左側、 頂端或中央按鈕的對齊按鈕文字。 在執行階段，您可以控制按鈕是否顯示文字、 影像或文字和影像。 您也可以指定特定的資料指標影像會顯示當游標停留在按鈕。  
  
 建立按鈕控制項，直接在程式碼，或使用**MFC 類別精靈**工具和對話方塊範本。 如果您直接建立的按鈕控制項，將`CMFCButton`變數與您的應用程式，然後呼叫建構函式和`Create`方法`CMFCButton`物件。 如果您使用**MFC 類別精靈**，加入`CButton`變數設為您的應用程式，然後變更變數的型別`CButton`到`CMFCButton`。  
  
 若要處理通知訊息方塊應用程式 對話方塊中的，加入訊息對應項目和每個通知的事件處理常式。 傳送的告知`CMFCButton`物件是由傳送那些相同`CButton`物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的設定按鈕的屬性`CMFCButton`類別。 範例是一部分[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&28;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&31;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls #&32;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls #&33;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxbutton.h  
  
##  <a name="cleanup"></a>CMFCButton::CleanUp  
 重設內部變數，並釋放已配置的資源，例如影像、 點陣圖和圖示。  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip  
 指定是否要在大型的工具提示視窗或截斷的版小工具提示視窗中的文字顯示完整的工具提示文字。  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bOn`  
 `TRUE`若要顯示的所有文字。`FALSE`要截斷的顯示文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont  
 指定按鈕文字的字型是相同的應用程式 功能表上的字型。  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bOn`  
 `TRUE`若要使用應用程式功能表字型為按鈕文字的字型。`FALSE`使用系統字型。 預設為 `TRUE`。  
  
 [in] `bRedraw`  
 `TRUE`若要立即重繪螢幕。否則， `FALSE`。 預設為 `TRUE`。  
  
### <a name="remarks"></a>備註  
 如果您不使用這個方法來指定按鈕文字的字型，您可以指定字型[CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont)方法。 如果您根本不指定字型，架構會設定預設字型。  
  
##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming  
 指定按鈕的框線樣式是否對應至目前的 Windows 佈景主題。  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`若要使用目前的 Windows 佈景主題來繪製按鈕的框線。`FALSE`為不使用 Windows 佈景主題。 預設為 `TRUE`。  
  
### <a name="remarks"></a>備註  
 這個方法會影響衍生自您的應用程式中的所有按鈕`CMFCButton`類別。  
  
##  <a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl  
 傳回基礎的工具提示控制項的參考。  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>傳回值  
 基礎的工具提示控制項的參考。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck  
 指出核取方塊或選項按鈕是否為自動的按鈕。  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕的，樣式 BS_AUTOCHECKBOX 或 BS_AUTORADIOBUTTON;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode  
 指出是否要將按鈕設定為自動重複模式。  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕設定為自動重複模式，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 使用[CMFCButton::SetAutorepeatMode](#setautorepeatmode)方法，將按鈕設定為自動重複模式。  
  
##  <a name="ischeckbox"></a>CMFCButton::IsCheckBox  
 表示按鈕是否為核取方塊按鈕。  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕有 BS_CHECKBOX 或 BS_AUTOCHECKBOX 樣式，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ischecked"></a>CMFCButton::IsChecked  
 指出是否要檢查目前的按鈕。  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已核取 [目前] 按鈕。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會使用不同的方式來指出會檢查不同種類的按鈕。 例如，選項按鈕已核取它包含了一個點。核取方塊時，它包含**X**。  
  
##  <a name="ishighlighted"></a>CMFCButton::IsHighlighted  
 表示按鈕會反白顯示。  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕會反白顯示，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 當滑鼠停留在按鈕上時，按鈕會變成反白顯示。  
  
##  <a name="ispressed"></a>CMFCButton::IsPressed  
 指出是否推入並反白顯示的按鈕。  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按下按鈕時，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ispushed"></a>CMFCButton::IsPushed  
 指出是否按下按鈕。  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按下按鈕，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isradiobutton"></a>CMFCButton::IsRadioButton  
 指出按鈕是否為選項按鈕。  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按鈕樣式 BS_RADIOBUTTON 或 BS_AUTORADIOBUTTON; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled  
 指出目前的 Windows 佈景主題是否對應按鈕的框線樣式。  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕的框線樣式對應至目前的 Windows 佈景主題。否則， `FALSE`。  
  
##  <a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus  
 指出是否要繪製焦點矩形按鈕周圍。  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>備註  
 設定`m_bDrawFocus`成員`TRUE`指定架構的焦點周圍繪製矩形按鈕的文字及影像如果按鈕取得焦點。  
  
 `CMFCButton` 建構函式會將此成員初始化為 `TRUE`。  
  
##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked  
 指出是否要將游標停留時，反白顯示 BS_CHECKBOX 樣式 按鈕。  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>備註  
 設定`m_bHighlightChecked`成員`TRUE`來指定當滑鼠停留在 framework 會標示 BS_CHECKBOX 樣式 按鈕。  
  
##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage  
 指出是否要在按鈕的右邊顯示影像。  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>備註  
 設定`m_bRightImage`成員`TRUE`指定架構，會顯示按鈕的影像按鈕的文字標籤的右側。  
  
##  <a name="m_btransparent"></a>CMFCButton::m_bTransparent  
 指出是否為透明的按鈕。  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>備註  
 設定`m_bTransparent`成員`TRUE`來指定，架構會讓按鈕變成透明。 `CMFCButton` 建構函式會將此成員初始化為 `FALSE`。  
  
##  <a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle  
 指定按鈕文字的對齊方式。  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>備註  
 使用下列其中一種`CMFCButton::AlignStyle`列舉值，來指定按鈕文字的對齊方式︰  
  
|值|描述|  
|-----------|-----------------|  
|ALIGN_CENTER|（預設值）將按鈕的中心按鈕文字的對齊。|  
|ALIGN_LEFT|對齊按鈕左邊的按鈕文字。|  
|ALIGN_RIGHT|將右側按鈕的按鈕文字的對齊。|  
  
 `CMFCButton`建構函式會初始化這個成員為 ALIGN_CENTER。  
  
##  <a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle  
 指定的按鈕，例如無框線、 一般，分號平面或 3D 樣式。  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>備註  
 下表列出`CMFCButton::m_nFlatStyle`列舉值，指定按鈕的外觀。  
  
|值|描述|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|（預設值）按鈕會出現具有高的&3;d 側邊。 按一下按鈕時，按鈕會出現深層的縮排到被按下。|  
|BUTTONSTYLE_FLAT|當滑鼠移至按鈕不會暫停時，似乎二維 按鈕，且沒有引發側邊。 當滑鼠停留在按鈕上時，按鈕會顯示有低的&3;d 側邊。 按一下按鈕時，按鈕會出現淺層縮排到被按下。|  
|BUTTONSTYLE_SEMIFLAT|按鈕會出現具有低的&3;d 側邊。 按一下按鈕時，按鈕會出現深層的縮排到被按下。|  
|BUTTONSTYLE_NOBORDERS|按鈕不會引發側邊，一律會顯示二維。 按鈕似乎未按下時會被放入縮排。|  
  
 `CMFCButton` 建構函式會將此成員初始化為 `BUTTONSTYLE_3D`。  
  
### <a name="example"></a>範例  
 下列範例示範如何設定的值`m_nFlatStyle`中的成員變數`CMFCButton`類別。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&28;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&29;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>CMFCButton::OnDraw  
 若要繪製按鈕架構呼叫。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 限定按鈕的矩形的參考。  
  
 [in] `uiState`  
 目前的按鈕狀態。 如需詳細資訊，請參閱`itemState`成員[DRAWITEMSTRUCT 結構](../../mfc/reference/drawitemstruct-structure.md)主題。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼來繪製按鈕。  
  
##  <a name="ondrawborder"></a>CMFCButton::OnDrawBorder  
 若要繪製按鈕的框線架構呼叫。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectClient`  
 限定按鈕的矩形的參考。  
  
 [in] `uiState`  
 目前的按鈕狀態。 如需詳細資訊，請參閱`itemState`成員[DRAWITEMSTRUCT 結構](../../mfc/reference/drawitemstruct-structure.md)主題。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼來繪製框線。  
  
##  <a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect  
 若要繪製焦點矩形按鈕架構呼叫。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectClient`  
 限定按鈕的矩形的參考。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼繪製焦點矩形。  
  
##  <a name="ondrawtext"></a>CMFCButton::OnDrawText  
 若要繪製按鈕文字架構呼叫。  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    const CRect& rect,  
    const CString& strText,  
    UINT uiDTFlags,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 限定按鈕的矩形的參考。  
  
 [in] `strText`  
 要繪製的文字。  
  
 [in] `uiDTFlags`  
 旗標，指定如何格式化的文字。 如需詳細資訊，請參閱`nFormat`參數[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法。  
  
 [in] `uiState`  
 （保留）。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼繪製按鈕文字。  
  
##  <a name="onfillbackground"></a>CMFCButton::OnFillBackground  
 若要繪製背景的按鈕文字架構呼叫。  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rectClient`  
 限定按鈕的矩形的參考。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法來繪製按鈕的背景使用您自己的程式碼。  
  
##  <a name="selectfont"></a>CMFCButton::SelectFont  
 擷取與指定之的裝置內容相關聯的字型。  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
### <a name="return-value"></a>傳回值  
 覆寫這個方法，以使用您自己的程式碼來擷取字型。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode  
 將按鈕設定為自動重複模式。  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTimeDelay`  
 非負的數字，指定傳送給父視窗的訊息之間的間隔。 以毫秒為單位的間隔，其預設值為 500 毫秒。 指定零可停用自動重複訊息模式。  
  
### <a name="remarks"></a>備註  
 這個方法會使持續傳送 WM_COMMAND 訊息給父視窗，直到放開按鍵時，按鈕或`nTimeDelay`參數設定為零。  
  
##  <a name="setcheckedimage"></a>CMFCButton::SetCheckedImage  
 設定已核取按鈕的影像。  
  
```  
void SetCheckedImage(
    HICON hIcon,  
    BOOL bAutoDestroy=TRUE,  
    HICON hIconHot=NULL,  
    HICON hIconDisabled=NULL,  
    BOOL bAlphaBlend=FALSE);

 
void SetCheckedImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy=TRUE,  
    HBITMAP hBitmapHot=NULL,  
    BOOL bMap3dColors=TRUE,  
    HBITMAP hBitmapDisabled=NULL);

 
void SetCheckedImage(
    UINT uiBmpResId,  
    UINT uiBmpHotResId=0,  
    UINT uiBmpDsblResID=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `hIcon`  
 包含點陣圖和新的映像的遮罩圖示的控制代碼。  
  
 [in] `bAutoDestroy`  
 `TRUE`若要指定點陣圖資源會自動; 終結否則， `FALSE`。 預設為 `TRUE`。  
  
 [in] `hIconHot`  
 包含所選取狀態影像的圖示的控制代碼。  
  
 [in] `hBitmap`  
 包含未選取狀態影像的點陣圖的控制代碼。  
  
 [in] `hBitmapHot`  
 包含所選取狀態影像的點陣圖的控制代碼。  
  
 [in] `bMap3dColors`  
 指定透明背景的色彩按鈕。也就是按鈕的圖示。 `TRUE`若要使用的色彩值 RGB （192，192，192）。`FALSE`使用所定義的色彩值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [in] `uiBmpResId`  
 未選取映像的資源識別碼。  
  
 [in] `uiBmpHotResId`  
 所選影像的資源識別碼。  
  
 [in] `hIconDisabled`  
 已停用的映像的圖示的控制代碼。  
  
 [in] `hBitmapDisabled`  
 包含已停用的映像的點陣圖的控制代碼。  
  
 [in] `uiBmpDsblResID`  
 已停用點陣圖資源識別碼。  
  
 [in] `bAlphaBlend`  
 `TRUE`若要使用 32 位元的映像使用 alpha 色頻。`FALSE`，而不使用 alpha 色頻的映像。 預設為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setfacecolor"></a>CMFCButton::SetFaceColor  
 設定按鈕文字的背景色彩。  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `crFace`  
 RGB 色彩值。  
  
 [in] `bRedraw`  
 `TRUE`若要立即; 重繪螢幕否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 使用這個方法來定義新的填滿色彩的按鈕背景 （圖示）。 請注意，不是背景填滿時[CMFCButton::m_bTransparent](#m_btransparent)成員變數是`TRUE`。  
  
##  <a name="setimage"></a>CMFCButton::SetImage  
 設定按鈕的影像。  
  
```  
void SetImage(
    HICON hIcon,  
    BOOL bAutoDestroy=TRUE,  
    HICON hIconHot=NULL,  
    HICON hIconDisabled=NULL,  
    BOOL bAlphaBlend=FALSE);

 
void SetImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy=TRUE,  
    HBITMAP hBitmapHot=NULL,  
    BOOL bMap3dColors=TRUE,  
    HBITMAP hBitmapDisabled=NULL);

 
void SetImage(
    UINT uiBmpResId,  
    UINT uiBmpHotResId=0,  
    UINT uiBmpDsblResID=0);
```  
  
### <a name="parameters"></a>參數  
 [in] `hIcon`  
 包含點陣圖和新的映像的遮罩圖示的控制代碼。  
  
 [in] `bAutoDestroy`  
 `TRUE`若要指定點陣圖資源會自動; 終結否則， `FALSE`。 預設為 `TRUE`。  
  
 [in] `hIconHot`  
 包含所選取狀態影像的圖示的控制代碼。  
  
 [in] `hBitmap`  
 包含未選取狀態影像的點陣圖的控制代碼。  
  
 [in] `hBitmapHot`  
 包含所選取狀態影像的點陣圖的控制代碼。  
  
 [in] `uiBmpResId`  
 未選取映像的資源識別碼。  
  
 [in] `uiBmpHotResId`  
 所選影像的資源識別碼。  
  
 [in] `bMap3dColors`  
 指定透明背景的色彩按鈕。也就是按鈕的圖示。 `TRUE`若要使用的色彩值 RGB （192，192，192）。`FALSE`使用所定義的色彩值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [in] `hIconDisabled`  
 已停用的映像的圖示的控制代碼。  
  
 [in] `hBitmapDisabled`  
 包含已停用的映像的點陣圖的控制代碼。  
  
 [in] `uiBmpDsblResID`  
 已停用點陣圖資源識別碼。  
  
 [in] `bAlphaBlend`  
 `TRUE`若要使用 32 位元的映像使用 alpha 色頻。`FALSE`，而不使用 alpha 色頻的映像。 預設為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
 下列範例示範如何使用各種版本`SetImage`方法中的`CMFCButton`類別。 範例是一部分[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&28;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&31;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor  
 設定資料指標的影像。  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>參數  
 [in] `hcursor`  
 資料指標控制代碼。  
  
### <a name="remarks"></a>備註  
 使用此方法將資料指標的映像，例如手狀游標，與按鈕。 游標會從應用程式資源載入。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetMouseCursor`方法中的`CMFCButton`類別。 此範例是中的程式碼的一部分[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&28;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&30;](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand  
 設定游標的左手邊的影像。  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>備註  
 使用這個方法與按鈕關聯的左手邊的游標映像。 游標會從應用程式資源載入。  
  
##  <a name="setstdimage"></a>CMFCButton::SetStdImage  
 使用`CMenuImages`物件來設定按鈕的影像。  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>參數  
 [in] `id`  
 其中一個按鈕影像識別項中定義`CMenuImage::IMAGES_IDS`列舉型別。 映像值指定映像，例如箭號、 pin，以及選項按鈕。  
  
 [in] `state`  
 其中一個按鈕影像狀態識別項中定義`CMenuImages::IMAGE_STATE`列舉型別。 映像狀態指定按鈕色彩，例如黑色、 灰色、 淺灰色白色與暗灰色。 預設值是 `CMenuImages::ImageBlack`。  
  
 [in] `idDisabled`  
 其中一個按鈕影像識別項中定義`CMenuImage::IMAGES_IDS`列舉型別。 映像表示按鈕已停用。 預設值是第一個按鈕影像 ( `CMenuImages::IdArrowDown`)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settextcolor"></a>CMFCButton::SetTextColor  
 設定未選取按鈕的按鈕文字的色彩。  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrText`  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor  
 設定已選取按鈕的按鈕文字的色彩。  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrTextHot`  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settooltip"></a>CMFCButton::SetTooltip  
 關聯按鈕的工具提示。  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszToolTipText`  
 工具提示文字指標。 請指定 NULL 來停用的工具提示。  
  
### <a name="remarks"></a>備註  
  
##  <a name="sizetocontent"></a>CMFCButton::SizeToContent  
 調整大小，以包含其按鈕文字和影像的按鈕。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bCalcOnly`  
 `TRUE`若要計算，但不是能變更的按鈕，新的大小`FALSE`若要變更按鈕的大小。 預設為 `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，其中包含新按鈕的大小。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法會計算新的大小，其中包含 10 個像素水平邊界和 5 像素的邊界。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl 類別](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)

