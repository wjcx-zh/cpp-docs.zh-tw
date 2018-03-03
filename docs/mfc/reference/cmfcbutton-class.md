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
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6d496cf079cd56d8260c5fd8072809bc05559ef2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcbutton-class"></a>CMFCButton 類別
`CMFCButton`類別將功能加入[CButton](../../mfc/reference/cbutton-class.md)類別，例如對齊按鈕文字、 結合按鈕文字和影像、 選取游標和指定工具提示。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCButton : public CButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCButton::CMFCButton`|預設建構函式。|  
|`CMFCButton::~CMFCButton`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCButton::CleanUp](#cleanup)|重設內部變數，並會釋放已配置的資源，例如影像、 點陣圖和圖示。|  
|`CMFCButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCButton::DrawItem`|當主控描繪按鈕的視覺外觀變更時由架構呼叫。 (覆寫[CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem)。)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|指定是否要顯示在大型的工具提示視窗或小工具提示視窗中的文字已截斷的版本的工具提示的全文檢索。|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|指定按鈕的文字字型是否與應用程式功能表字型相同。|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|指定按鈕框線的樣式是否對應至目前的 Windows 佈景主題。|  
|`CMFCButton::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|傳回之基礎的工具提示控制項的參考。|  
|[CMFCButton::IsAutoCheck](#isautocheck)|指出核取方塊或選項按鈕是否為自動的按鈕。|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|表示按鈕是否設定為自動重複模式。|  
|[CMFCButton::IsCheckBox](#ischeckbox)|表示按鈕是否核取方塊按鈕。|  
|[CMFCButton::IsChecked](#ischecked)|指出是否要檢查目前的按鈕。|  
|[CMFCButton::IsHighlighted](#ishighlighted)|表示按鈕會反白顯示。|  
|[CMFCButton::IsPressed](#ispressed)|表示按鈕是否為推入，並反白顯示。|  
|[CMFCButton::IsPushed](#ispushed)|指出是否按下按鈕。|  
|[CMFCButton::IsRadioButton](#isradiobutton)|表示按鈕是否選項按鈕。|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|表示按鈕框線的樣式是否與目前的 Windows 佈景主題。|  
|`CMFCButton::OnDrawParentBackground`|在指定的區域中繪製按鈕的父系的背景。 (覆寫[AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|將視窗訊息轉譯分派至之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|將按鈕設定為自動重複模式。|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|設定為已核取按鈕的影像。|  
|[CMFCButton::SetFaceColor](#setfacecolor)|設定按鈕文字的背景色彩。|  
|[CMFCButton::SetImage](#setimage)|設定按鈕的影像。|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|設定資料指標影像。|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|將資料指標設定為一隻手上的映像。|  
|[CMFCButton::SetStdImage](#setstdimage)|使用`CMenuImages`物件來設定按鈕影像。|  
|[CMFCButton::SetTextColor](#settextcolor)|設定未選取按鈕的按鈕文字的色彩。|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|設定選取的按鈕的按鈕文字的色彩。|  
|[CMFCButton::SetTooltip](#settooltip)|關聯按鈕的工具提示。|  
|[CMFCButton::SizeToContent](#sizetocontent)|調整大小的按鈕，以包含其按鈕文字和影像。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|由架構呼叫以繪製按鈕。|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|由架構呼叫以繪製按鈕的框線。|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|由架構呼叫以繪製焦點矩形的按鈕。|  
|[CMFCButton::OnDrawText](#ondrawtext)|由架構呼叫以繪製按鈕的文字。|  
|[CMFCButton::OnFillBackground](#onfillbackground)|由架構呼叫以繪製背景的按鈕文字。|  
|[CMFCButton::SelectFont](#selectfont)|擷取與指定的裝置內容相關聯的字型。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|指出是否要繪製焦點矩形以圍繞 按鈕。|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|指出是否要游標上方時，反白顯示 BS_CHECKBOX 樣式 按鈕。|  
|[CMFCButton::m_bRightImage](#m_brightimage)|表示是否顯示按鈕右邊的映像。|  
|[CMFCButton::m_bTransparent](#m_btransparent)|表示按鈕是否是透明的。|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|指定按鈕文字的對齊方式。|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|指定的按鈕，例如無框線的一般，以平面或 3D 樣式。|  
  
## <a name="remarks"></a>備註  
 按鈕的其他類型都會衍生自`CMFCButton`類別，例如[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)類別，可支援超連結，而`CMFCColorButton`類別，可支援色彩選擇器對話方塊。  
  
 樣式`CMFCButton`物件可以是*3D*，*一般*，*分號一般*或*無框線*。 按鈕文字可以靠左、 top 或 center 的按鈕。 在執行階段，您可以控制按鈕顯示的文字、 影像或文字和影像。 您也可以指定資料指標停留在按鈕時，顯示特定資料指標的映像。  
  
 建立按鈕控制項，直接在程式碼，或使用**MFC 類別精靈**工具和對話方塊範本。 如果您直接建立按鈕控制項，加入`CMFCButton`變數設為您的應用程式，然後再呼叫建構函式和`Create`方法`CMFCButton`物件。 如果您使用**MFC 類別精靈**，新增`CButton`變數設為您的應用程式，然後變更 來自變數的型別`CButton`至`CMFCButton`。  
  
 若要處理對話方塊方塊中的應用程式中的通知訊息，新增訊息對應項目和每個通知的事件處理常式。 所傳送的通知`CMFCButton`物件是由傳送那些相同`CButton`物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的設定按鈕的屬性`CMFCButton`類別。 此範例是一部分[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxbutton.h  
  
##  <a name="cleanup"></a>CMFCButton::CleanUp  
 重設內部變數，並會釋放已配置的資源，例如影像、 點陣圖和圖示。  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip  
 指定是否要顯示在大型的工具提示視窗或小工具提示視窗中的文字已截斷的版本的工具提示的全文檢索。  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bOn`  
 `TRUE`若要顯示的所有文字。`FALSE`要截斷的顯示文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont  
 指定按鈕的文字字型是否與應用程式功能表字型相同。  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bOn`  
 `TRUE`若要使用應用程式功能表字型為按鈕的文字字型。`FALSE`使用系統字型。 預設值為 `TRUE`。  
  
 [輸入] `bRedraw`  
 `TRUE`若要立即重繪螢幕。否則， `FALSE`。 預設值為 `TRUE`。  
  
### <a name="remarks"></a>備註  
 如果您不使用這個方法來指定按鈕的文字字型，您可以指定與字型[CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont)方法。 如果您不在指定的字型，架構就會設定預設字型。  
  
##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming  
 指定按鈕框線的樣式是否對應至目前的 Windows 佈景主題。  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE`若要使用目前的 Windows 佈景主題來繪製按鈕的框線;`FALSE`為不使用 Windows 佈景主題。 預設值為 `TRUE`。  
  
### <a name="remarks"></a>備註  
 這個方法會影響您衍生自的應用程式中的所有按鈕`CMFCButton`類別。  
  
##  <a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl  
 傳回之基礎的工具提示控制項的參考。  
  
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
 表示按鈕是否設定為自動重複模式。  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕設定為自動重複模式，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 使用[CMFCButton::SetAutorepeatMode](#setautorepeatmode)方法將按鈕設定成自動重複模式。  
  
##  <a name="ischeckbox"></a>CMFCButton::IsCheckBox  
 表示按鈕是否核取方塊按鈕。  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果按鈕 BS_CHECKBOX 或 BS_AUTOCHECKBOX 樣式，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ischecked"></a>CMFCButton::IsChecked  
 指出是否要檢查目前的按鈕。  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已核取 [目前] 按鈕。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 架構會使用不同的方式來表示已簽不同種類的按鈕。 當它包含小數點，比方說，選取選項按鈕核取方塊時，它包含**X**。  
  
##  <a name="ishighlighted"></a>CMFCButton::IsHighlighted  
 表示按鈕會反白顯示。  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按鈕會反白顯示; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 當滑鼠停留在按鈕上時，會反白顯示的按鈕。  
  
##  <a name="ispressed"></a>CMFCButton::IsPressed  
 表示按鈕是否為推入，並反白顯示。  
  
```  
BOOL IsPressed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按下按鈕; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="ispushed"></a>CMFCButton::IsPushed  
 指出是否按下按鈕。  
  
```  
BOOL IsPushed() const;  
```  
  
### <a name="return-value"></a>傳回值  
 按下按鈕; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="isradiobutton"></a>CMFCButton::IsRadioButton  
 表示按鈕是否選項按鈕。  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>傳回值  
 將按鈕樣式 BS_RADIOBUTTON 或 BS_AUTORADIOBUTTON; 如果為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
  
##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled  
 表示按鈕框線的樣式是否與目前的 Windows 佈景主題。  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果按鈕框線的樣式會對應至目前的 Windows 佈景主題;否則， `FALSE`。  
  
##  <a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus  
 指出是否要繪製焦點矩形以圍繞 按鈕。  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>備註  
 設定`m_bDrawFocus`成員`TRUE`指定架構的繪製焦點矩形以圍繞按鈕的文字及影像如果按鈕焦點。  
  
 `CMFCButton` 建構函式會將此成員初始化為 `TRUE`。  
  
##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked  
 指出是否要游標上方時，反白顯示 BS_CHECKBOX 樣式 按鈕。  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>備註  
 設定`m_bHighlightChecked`成員`TRUE`來指定，架構會反白顯示 BS_CHECKBOX 樣式 按鈕的滑鼠停留時。  
  
##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage  
 表示是否顯示按鈕右邊的映像。  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>備註  
 設定`m_bRightImage`成員`TRUE`指定架構，會顯示按鈕的影像右邊的按鈕的文字標籤。  
  
##  <a name="m_btransparent"></a>CMFCButton::m_bTransparent  
 表示按鈕是否是透明的。  
  
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
 使用下列其中一種`CMFCButton::AlignStyle`列舉值，來指定按鈕文字的對齊方式：  
  
|值|描述|  
|-----------|-----------------|  
|ALIGN_CENTER|（預設值）將按鈕的中心按鈕文字對齊。|  
|ALIGN_LEFT|將左側按鈕的按鈕文字對齊。|  
|ALIGN_RIGHT|對齊按鈕右邊的按鈕文字。|  
  
 `CMFCButton`建構函式會初始化這個成員為 ALIGN_CENTER。  
  
##  <a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle  
 指定的按鈕，例如無框線的一般，以平面或 3D 樣式。  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>備註  
 下表列出`CMFCButton::m_nFlatStyle`列舉值，指定按鈕的外觀。  
  
|值|描述|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|（預設值）按鈕會出現具有高的 3d 側邊。 按一下按鈕時，按鈕會出現按到深層縮排。|  
|BUTTONSTYLE_FLAT|當滑鼠停留在按鈕不會暫停時，按鈕會顯示為二維，而且沒有引發側邊。 當滑鼠停留在按鈕時，按鈕會出現具有低的 3d 側邊。 按一下按鈕時，按鈕會出現按到淺層縮排。|  
|BUTTONSTYLE_SEMIFLAT|按鈕會出現具有低的 3d 側邊。 按一下按鈕時，按鈕會出現按到深層縮排。|  
|BUTTONSTYLE_NOBORDERS|按鈕不會引發側邊，並一律會顯示二維。 按一下時其按縮排成不 按鈕。|  
  
 `CMFCButton` 建構函式會將此成員初始化為 `BUTTONSTYLE_3D`。  
  
### <a name="example"></a>範例  
 下列範例示範如何設定的值`m_nFlatStyle`中的成員變數`CMFCButton`類別。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>CMFCButton::OnDraw  
 由架構呼叫以繪製按鈕。  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
 [輸入] `rect`  
 參考範圍按鈕的矩形。  
  
 [輸入] `uiState`  
 目前的按鈕狀態。 如需詳細資訊，請參閱`itemState`隸屬[DRAWITEMSTRUCT 結構](../../mfc/reference/drawitemstruct-structure.md)主題。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼繪製按鈕。  
  
##  <a name="ondrawborder"></a>CMFCButton::OnDrawBorder  
 由架構呼叫以繪製按鈕的框線。  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
 [輸入] `rectClient`  
 參考範圍按鈕的矩形。  
  
 [輸入] `uiState`  
 目前的按鈕狀態。 如需詳細資訊，請參閱`itemState`隸屬[DRAWITEMSTRUCT 結構](../../mfc/reference/drawitemstruct-structure.md)主題。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼來繪製框線。  
  
##  <a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect  
 由架構呼叫以繪製焦點矩形的按鈕。  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
 [輸入] `rectClient`  
 參考範圍按鈕的矩形。  
  
### <a name="remarks"></a>備註  
 若要使用自己的程式碼繪製焦點矩形，這個方法會覆寫。  
  
##  <a name="ondrawtext"></a>CMFCButton::OnDrawText  
 由架構呼叫以繪製按鈕的文字。  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    const CRect& rect,  
    const CString& strText,  
    UINT uiDTFlags,  
    UINT uiState);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
 [輸入] `rect`  
 參考範圍按鈕的矩形。  
  
 [輸入] `strText`  
 要繪製的文字。  
  
 [輸入] `uiDTFlags`  
 旗標，指定如何格式化的文字。 如需詳細資訊，請參閱`nFormat`參數[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法。  
  
 [輸入] `uiState`  
 （保留）。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼繪製按鈕的文字。  
  
##  <a name="onfillbackground"></a>CMFCButton::OnFillBackground  
 由架構呼叫以繪製背景的按鈕文字。  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
 [輸入] `rectClient`  
 參考範圍按鈕的矩形。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以使用您自己的程式碼繪製按鈕的背景。  
  
##  <a name="selectfont"></a>CMFCButton::SelectFont  
 擷取與指定的裝置內容相關聯的字型。  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pDC`  
 裝置內容的指標。  
  
### <a name="return-value"></a>傳回值  
 覆寫這個方法，以使用您自己的程式碼擷取字型。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode  
 將按鈕設定為自動重複模式。  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nTimeDelay`  
 非負的數字，指定傳送至父視窗的訊息之間的間隔。 以毫秒為單位的間隔，其預設值為 500 毫秒。 指定 0 時可停用自動重複訊息模式。  
  
### <a name="remarks"></a>備註  
 這個方法會使按鈕不斷地傳送至父視窗 WM_COMMAND 訊息，直到放開按鈕，或`nTimeDelay`參數設為零。  
  
##  <a name="setcheckedimage"></a>CMFCButton::SetCheckedImage  
 設定為已核取按鈕的影像。  
  
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
 [輸入] `hIcon`  
 點陣圖和新的映像的遮罩包含圖示的控制代碼。  
  
 [輸入] `bAutoDestroy`  
 `TRUE`若要指定點陣圖資源會自動; 終結否則， `FALSE`。 預設值為 `TRUE`。  
  
 [輸入] `hIconHot`  
 包含所選取狀態的影像圖示的控制代碼。  
  
 [輸入] `hBitmap`  
 包含未選取狀態的影像之點陣圖的控制代碼。  
  
 [輸入] `hBitmapHot`  
 包含所選取狀態的影像之點陣圖的控制代碼。  
  
 [輸入] `bMap3dColors`  
 指定透明背景的色彩按鈕。也就是說，按鈕的圖示。 `TRUE`若要使用的色彩值 RGB （192、 192，192）;`FALSE`使用所定義的色彩值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [輸入] `uiBmpResId`  
 未選取的映像的資源識別碼。  
  
 [輸入] `uiBmpHotResId`  
 所選影像的資源識別碼。  
  
 [輸入] `hIconDisabled`  
 已停用映像的圖示的控制代碼。  
  
 [輸入] `hBitmapDisabled`  
 包含已停用的影像之點陣圖的控制代碼。  
  
 [輸入] `uiBmpDsblResID`  
 已停用點陣圖的資源識別碼。  
  
 [輸入] `bAlphaBlend`  
 `TRUE`若要使用使用 alpha 色板; 只有 32 位元映像`FALSE`，若要不使用只能包含影像 alpha 色板。 預設值為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="setfacecolor"></a>CMFCButton::SetFaceColor  
 設定按鈕文字的背景色彩。  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `crFace`  
 RGB 色彩值。  
  
 [輸入] `bRedraw`  
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
 [輸入] `hIcon`  
 點陣圖和新的映像的遮罩包含圖示的控制代碼。  
  
 [輸入] `bAutoDestroy`  
 `TRUE`若要指定點陣圖資源會自動; 終結否則， `FALSE`。 預設值為 `TRUE`。  
  
 [輸入] `hIconHot`  
 包含所選取狀態的影像圖示的控制代碼。  
  
 [輸入] `hBitmap`  
 包含未選取狀態的影像之點陣圖的控制代碼。  
  
 [輸入] `hBitmapHot`  
 包含所選取狀態的影像之點陣圖的控制代碼。  
  
 [輸入] `uiBmpResId`  
 未選取的映像的資源識別碼。  
  
 [輸入] `uiBmpHotResId`  
 所選影像的資源識別碼。  
  
 [輸入] `bMap3dColors`  
 指定透明背景的色彩按鈕。也就是說，按鈕的圖示。 `TRUE`若要使用的色彩值 RGB （192、 192，192）;`FALSE`使用所定義的色彩值`AFX_GLOBAL_DATA::clrBtnFace`。  
  
 [輸入] `hIconDisabled`  
 已停用映像的圖示的控制代碼。  
  
 [輸入] `hBitmapDisabled`  
 包含已停用的影像之點陣圖的控制代碼。  
  
 [輸入] `uiBmpDsblResID`  
 已停用點陣圖的資源識別碼。  
  
 [輸入] `bAlphaBlend`  
 `TRUE`若要使用使用 alpha 色板; 只有 32 位元映像`FALSE`，若要不使用只能包含影像 alpha 色板。 預設值為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
### <a name="example"></a>範例  
 下列範例示範如何使用各種版本的`SetImage`方法中的`CMFCButton`類別。 此範例是一部分[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor  
 設定資料指標影像。  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `hcursor`  
 資料指標的控制代碼。  
  
### <a name="remarks"></a>備註  
 使用這個方法，使資料指標的映像，例如手狀游標，與按鈕。 游標會從應用程式資源載入。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`SetMouseCursor`方法中的`CMFCButton`類別。 此範例是中的程式碼的一部分[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand  
 將資料指標設定為一隻手上的映像。  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法將變成手的形狀的游標影像與按鈕產生關聯。 游標會從應用程式資源載入。  
  
##  <a name="setstdimage"></a>CMFCButton::SetStdImage  
 使用`CMenuImages`物件來設定按鈕影像。  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `id`  
 其中一個按鈕影像識別項中定義`CMenuImage::IMAGES_IDS`列舉型別。 指定的映像值，例如箭號、 pin 碼，以及選項按鈕的影像。  
  
 [輸入] `state`  
 其中一個按鈕影像狀態識別項中定義`CMenuImages::IMAGE_STATE`列舉型別。 映像狀態指定的按鈕色彩，例如黑色、 灰色、 淺灰色，白色與暗灰色。 預設值是 `CMenuImages::ImageBlack`。  
  
 [輸入] `idDisabled`  
 其中一個按鈕影像識別項中定義`CMenuImage::IMAGES_IDS`列舉型別。 映像表示按鈕已停用。 預設值是第一個按鈕影像 ( `CMenuImages::IdArrowDown`)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settextcolor"></a>CMFCButton::SetTextColor  
 設定未選取按鈕的按鈕文字的色彩。  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `clrText`  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor  
 設定選取的按鈕的按鈕文字的色彩。  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `clrTextHot`  
 RGB 色彩值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="settooltip"></a>CMFCButton::SetTooltip  
 關聯按鈕的工具提示。  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszToolTipText`  
 工具提示的文字指標。 請指定 NULL 來停用工具提示。  
  
### <a name="remarks"></a>備註  
  
##  <a name="sizetocontent"></a>CMFCButton::SizeToContent  
 調整大小的按鈕，以包含其按鈕文字和影像。  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bCalcOnly`  
 `TRUE`若要計算，但不是能變更的按鈕; 新的大小`FALSE`若要變更按鈕的大小。 預設值為 `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，其中包含新按鈕的大小。  
  
### <a name="remarks"></a>備註  
 根據預設，這個方法會計算新的大小，其中包含 10 個像素水平邊界和 5 像素的垂直邊界。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl 類別](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)
