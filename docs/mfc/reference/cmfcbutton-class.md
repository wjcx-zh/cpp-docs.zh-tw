---
title: CMFCButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 08/28/2018
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9acae5f87223a3b23c492f02596452fabb745f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441287"
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
|[CMFCButton::CleanUp](#cleanup)|重設內部變數，並釋放已配置的資源，例如影像、 點陣圖和圖示。|
|`CMFCButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCButton::DrawItem`|當主控描繪按鈕的視覺外觀變更時由架構呼叫。 (覆寫[CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem)。)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|指定是否要在大型的工具提示視窗或小型的工具提示視窗中的文字的截斷的版本顯示為工具提示的全文檢索。|
|[CMFCButton::EnableMenuFont](#enablemenufont)|指定按鈕的文字字型是否為相同應用程式功能表字型。|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|指定按鈕框線的樣式是否對應至目前的 Windows 佈景主題。|
|`CMFCButton::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|傳回基礎的工具提示控制項的參考。|
|[CMFCButton::IsAutoCheck](#isautocheck)|指出核取方塊或選項按鈕是否為自動的按鈕。|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|指出是否要將按鈕設定為自動重複模式。|
|[CMFCButton::IsCheckBox](#ischeckbox)|表示按鈕是否核取方塊按鈕。|
|[CMFCButton::IsChecked](#ischecked)|指出是否要檢查目前的按鈕。|
|[CMFCButton::IsHighlighted](#ishighlighted)|表示一個按鈕會反白顯示。|
|[CMFCButton::IsPressed](#ispressed)|表示一個按鈕是推送並反白顯示。|
|[CMFCButton::IsPushed](#ispushed)|指出是否按下按鈕。|
|[CMFCButton::IsRadioButton](#isradiobutton)|指出按鈕是否為選項按鈕。|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|指出按鈕框線的樣式是否對應至目前的 Windows 佈景主題。|
|`CMFCButton::OnDrawParentBackground`|在指定的區域中繪製按鈕的父代背景。 (覆寫[AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|將轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|將按鈕設定為自動重複模式。|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|設定核取按鈕的影像。|
|[CMFCButton::SetFaceColor](#setfacecolor)|設定按鈕文字的背景色彩。|
|[CMFCButton::SetImage](#setimage)|設定按鈕的影像。|
|[CMFCButton::SetMouseCursor](#setmousecursor)|設定資料指標的影像。|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|指針的映像中設定資料指標。|
|[CMFCButton::SetStdImage](#setstdimage)|使用`CMenuImages`物件來設定按鈕的影像。|
|[CMFCButton::SetTextColor](#settextcolor)|設定未選取按鈕的按鈕文字的色彩。|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|設定已選取按鈕的按鈕文字的色彩。|
|[CMFCButton::SetTooltip](#settooltip)|關聯 按鈕的工具提示。|
|[CMFCButton::SizeToContent](#sizetocontent)|調整大小的按鈕，以包含其按鈕文字和影像。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|由架構呼叫以繪製按鈕。|
|[CMFCButton::OnDrawBorder](#ondrawborder)|由架構呼叫以繪製按鈕的框線。|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|由架構呼叫以繪製焦點矩形的按鈕。|
|[CMFCButton::OnDrawText](#ondrawtext)|由架構呼叫以繪製按鈕的文字。|
|[CMFCButton::OnFillBackground](#onfillbackground)|由架構呼叫以繪製按鈕文字的背景。|
|[CMFCButton::SelectFont](#selectfont)|擷取與指定的裝置內容相關聯的字型。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|指定按鈕文字的對齊方式。|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|指定是否要使用 Windows XP 佈景主題。|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|指出是否要繪製焦點矩形的按鈕周圍。|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|指定按鈕，例如無框線、 一般，半平面或 3D 的樣式。|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|若為 TRUE，可讓要繪製為灰色的已停用的按鈕。|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|指出是否要將游標停留在其上方時，將 BS_CHECKBOX 樣式按鈕反白顯示。|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|指出是否要回應按下事件。|
|[CMFCButton::m_bRightImage](#m_brightimage)|指出是否要顯示按鈕右邊的 映像。|
|[CMFCButton::m_bTopImage](#m_bTopImage)| 指出影像是否在按鈕上。|
|[CMFCButton::m_bTransparent](#m_btransparent)|指出按鈕是否為透明。|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| 指出過去按一下事件是否按兩下。|

## <a name="remarks"></a>備註

其他類型的按鈕衍生自`CMFCButton`類別，例如[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)類別，可支援超連結，而`CMFCColorButton`類別，可支援色彩選擇器對話方塊。

樣式`CMFCButton`物件可以是*3D*，*一般*，*半平面*或是*無框線*。 按鈕文字可以靠左、 top 或 center 的按鈕。 在執行階段，您可以控制按鈕是否顯示文字、 影像或文字和影像。 您也可以指定當游標停留在按鈕時，會顯示特定的資料指標的影像。

直接在您的程式碼，或使用建立的按鈕控制項**MFC 類別精靈**工具和對話方塊範本。 如果您直接建立的按鈕控制項，將`CMFCButton`到您的應用程式，然後呼叫建構函式的變數和`Create`方法`CMFCButton`物件。 如果您使用**MFC 類別精靈**，新增`CButton`變數設為您的應用程式，然後變更 來自變數的型別`CButton`到`CMFCButton`。

若要處理對話方塊的 box 應用程式中的通知訊息，新增訊息對應項目和每個通知的事件處理常式。 所傳送的通知`CMFCButton`物件是由傳送那些相同`CButton`物件。

## <a name="example"></a>範例

下列範例示範如何使用中的各種方法來設定按鈕的內容`CMFCButton`類別。 範例是一部分[新的控制項範例](../../visual-cpp-samples.md)。

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

##  <a name="cleanup"></a>  CMFCButton::CleanUp

重設內部變數，並釋放已配置的資源，例如影像、 點陣圖和圖示。

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip

指定是否要在大型的工具提示視窗或小型的工具提示視窗中的文字的截斷的版本顯示為工具提示的全文檢索。

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
[in]True 表示要顯示的所有文字;要截斷的顯示文字，則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont

指定按鈕的文字字型是否為相同應用程式功能表字型。

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
[in]若要使用的應用程式功能表字型為按鈕文字的字型;，則為 TRUE使用系統字型，則為 FALSE。 預設值為 TRUE。

*bRedraw*<br/>
[in]若要立即重繪螢幕; TRUE否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

如果您不使用這個方法來指定按鈕文字的字型，您可以指定字型[CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont)方法。 如果您未完全指定字型，架構就會設定預設字型。

##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming

指定按鈕框線的樣式是否對應至目前的 Windows 佈景主題。

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]若要使用目前的 Windows 佈景主題來繪製按鈕框線;，則為 TRUE如果為 false，則不使用 Windows 佈景主題。 預設值為 TRUE。

### <a name="remarks"></a>備註

這個方法會影響您衍生自的應用程式中的所有按鈕`CMFCButton`類別。

##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl

傳回基礎的工具提示控制項的參考。

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>傳回值

基礎的工具提示控制項的參考。

### <a name="remarks"></a>備註

##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck

指出核取方塊或選項按鈕是否為自動的按鈕。

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>傳回值

如果按鈕的樣式，則為 TRUE BS_AUTOCHECKBOX 或 BS_AUTORADIOBUTTON;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode

指出是否要將按鈕設定為自動重複模式。

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>傳回值

如果按鈕設定為自動重複模式，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

使用[CMFCButton::SetAutorepeatMode](#setautorepeatmode)將按鈕設定為自動重複模式的方法。

##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox

表示按鈕是否核取方塊按鈕。

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>傳回值

如果按鈕有 BS_CHECKBOX 或 BS_AUTOCHECKBOX 樣式，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="ischecked"></a>  CMFCButton::IsChecked

指出是否要檢查目前的按鈕。

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>傳回值

如果已選取 [目前] 按鈕，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

架構會使用不同的方式，來指出會檢查不同種類的按鈕。 比方說，選項按鈕已核取它包含點;它包含時，系統會檢查核取方塊**X**。

##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted

表示一個按鈕會反白顯示。

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>傳回值

如果按鈕已反白顯示;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

當滑鼠停留在按鈕上時，按鈕會變成反白顯示。

##  <a name="ispressed"></a>  CMFCButton::IsPressed

表示一個按鈕是推送並反白顯示。

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>傳回值

如果按下按鈕時，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="ispushed"></a>  CMFCButton::IsPushed

指出是否按下按鈕。

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>傳回值

如果推入 按鈕，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton

指出按鈕是否為選項按鈕。

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>傳回值

將按鈕樣式是否 BS_RADIOBUTTON 或 BS_AUTORADIOBUTTON;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled

指出按鈕框線的樣式是否對應至目前的 Windows 佈景主題。

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>傳回值

如果目前的 Windows 佈景主題; 的對應按鈕框線的樣式，則為 TRUE。否則為 FALSE。



## <a name="a-namembdontusewinxptheme-cmfcbuttonmbdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/> CMFCButton::m_bDontUseWinXPTheme

指定是否要繪製按鈕時，使用 Windows XP 佈景主題。

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus

指出是否要繪製焦點矩形的按鈕周圍。

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>備註

設定`m_bDrawFocus`指定架構將焦點周圍繪製矩形按鈕的文字和影像按鈕焦點。 如果為 TRUE 的成員。

`CMFCButton`建構函式初始化這個成員為 TRUE。

##  <a name="m_bGrayDisabled"></a>  CMFCButton::m_bGrayDisabled

若為 TRUE，可讓要繪製為灰色的已停用的按鈕。


```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked

指出是否要將游標停留在其上方時，將 BS_CHECKBOX 樣式按鈕反白顯示。

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>備註

設定`m_bHighlightChecked`設為 TRUE，架構會反白顯示 BS_CHECKBOX 樣式按鈕的滑鼠停留在其上方時所指定的成員。

##  <a name="m_bResponseOnButtonDown"></a> CMFCButton::m_bResponseOnButtonDown

指出是否要回應按下事件。

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage

指出是否要顯示按鈕右邊的 映像。

```
BOOL m_bRightImage;
```


##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)

指出影像是否在按鈕上。

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>備註

設定`m_bRightImage`成員設為 TRUE，指定架構，會顯示為按鈕的影像右邊的按鈕的文字標籤。

##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent

指出按鈕是否為透明。

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>備註

設定`m_bTransparent`成員設為 TRUE 可指定，架構會讓按鈕變成透明。 `CMFCButton`建構函式初始化這個成員為 FALSE。

##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle

指定按鈕文字的對齊方式。

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>備註

使用下列其中一種`CMFCButton::AlignStyle`列舉值，來指定按鈕文字的對齊方式：

|值|描述|
|-----------|-----------------|
|ALIGN_CENTER|（預設值）將按鈕的中心按鈕文字的對齊。|
|ALIGN_LEFT|將左側按鈕的按鈕文字的對齊。|
|ALIGN_RIGHT|對齊按鈕右邊的按鈕文字。|

`CMFCButton`建構函式初始化這個成員為 ALIGN_CENTER。

##  <a name="m_bWasDblClk"></a>  CMFCButton::m_bWasDblClk](#m_bWasDblClk) |

指出事件是否按一下最後一個按兩下。 |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle

指定按鈕，例如無框線、 一般，半平面或 3D 的樣式。

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>備註

下表列出`CMFCButton::m_nFlatStyle`列舉值，指定按鈕的外觀。

|值|描述|
|-----------|-----------------|
|BUTTONSTYLE_3D|（預設值）按鈕隨即顯示具有高，三維的側邊。 按一下按鈕時，按鈕會出現相當於按到深入的縮排。|
|BUTTONSTYLE_FLAT|當滑鼠不會暫停按鈕上方時，按鈕似乎是二維，而且沒有引發的側邊。 當滑鼠停留在按鈕時，按鈕會似乎有低，三維的側邊。 當按一下按鈕時，按鈕會出現淺層縮排到被按下。|
|BUTTONSTYLE_SEMIFLAT|按鈕會出現有低，三維的側邊。 按一下按鈕時，按鈕會出現相當於按到深入的縮排。|
|BUTTONSTYLE_NOBORDERS|按鈕不會引發側邊，並一律會顯示二維。 按一下時，縮排成按似乎不到按鈕。|

`CMFCButton`建構函式初始化這個成員為 BUTTONSTYLE_3D。

### <a name="example"></a>範例

下列範例示範如何設定的值`m_nFlatStyle`中的成員變數`CMFCButton`類別。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

##  <a name="ondraw"></a>  CMFCButton::OnDraw

由架構呼叫以繪製按鈕。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rect*<br/>
[in]參考之按鈕的界限的矩形。

*uiState*<br/>
[in]目前的按鈕狀態。 如需詳細資訊，請參閱 <<c0> `itemState` 隸屬[DRAWITEMSTRUCT 結構](../../mfc/reference/drawitemstruct-structure.md)主題。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼來繪製按鈕。

##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder

由架構呼叫以繪製按鈕的框線。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rectClient*<br/>
[in]參考之按鈕的界限的矩形。

*uiState*<br/>
[in]目前的按鈕狀態。 如需詳細資訊，請參閱 <<c0> `itemState` 隸屬[DRAWITEMSTRUCT 結構](../../mfc/reference/drawitemstruct-structure.md)主題。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼來繪製框線。

##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect

由架構呼叫以繪製焦點矩形的按鈕。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rectClient*<br/>
[in]參考之按鈕的界限的矩形。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼來繪製焦點矩形。

##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText

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

*pDC*<br/>
[in]裝置內容指標。

*rect*<br/>
[in]參考之按鈕的界限的矩形。

*先把 strText*<br/>
[in]要繪製的文字。

*uiDTFlags*<br/>
[in]指定如何格式化文字的旗標。 如需詳細資訊，請參閱 < *nFormat*的參數[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法。

*uiState*<br/>
[in]保留。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼繪製按鈕的文字。

##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground

由架構呼叫以繪製按鈕文字的背景。

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

*rectClient*<br/>
[in]參考之按鈕的界限的矩形。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼繪製按鈕的背景。

##  <a name="selectfont"></a>  CMFCButton::SelectFont

擷取與指定的裝置內容相關聯的字型。

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容指標。

### <a name="return-value"></a>傳回值

覆寫這個方法，以使用您自己的程式碼來擷取字型。

### <a name="remarks"></a>備註

##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode

將按鈕設定為自動重複模式。

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>參數

*nTimeDelay*<br/>
[in]指定傳送至父視窗的訊息之間的間隔的非負值數字。 以毫秒為單位的間隔，其預設值為 500 毫秒。 指定 0 時可停用自動重複訊息模式。

### <a name="remarks"></a>備註

這個方法會導致不斷將 WM_COMMAND 訊息傳送至父視窗，直到放開按鈕，按鈕或*nTimeDelay*參數設為零。

##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage

設定核取按鈕的影像。

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

*hIcon*<br/>
[in]包含點陣圖和新的映像的遮罩的圖示的控制代碼。

*bAutoDestroy*<br/>
[in]若要指定點陣圖的資源會自動; 終結，則為 TRUE否則為 FALSE。 預設值為 TRUE。

*hIconHot*<br/>
[in]包含所選的狀態影像的圖示的控制代碼。

*hBitmap*<br/>
[in]包含未選取狀態的影像之點陣圖的控制代碼。

*hBitmapHot*<br/>
[in]包含所選狀態的影像之點陣圖的控制代碼。

*bMap3dColors*<br/>
[in]指定透明背景的色彩按鈕;也就是表面的按鈕。 若要使用的色彩值 RGB （192，192，192;），則為 TRUE若要使用所定義的色彩值，則為 FALSE `AFX_GLOBAL_DATA::clrBtnFace`。

*uiBmpResId*<br/>
[in]非選取的映像的資源識別碼。

*uiBmpHotResId*<br/>
[in]選取的映像的資源識別碼。

*hIconDisabled*<br/>
[in]已停用的映像的圖示的控制代碼。

*hBitmapDisabled*<br/>
[in]包含已停用的影像之點陣圖的控制代碼。

*uiBmpDsblResID*<br/>
[in]已停用點陣圖的資源識別碼。

*bAlphaBlend*<br/>
[in]若為 true，則使用 alpha 色板; 的使用僅 32 位元映像設為 FALSE，使用只有 alpha 色頻影像。 預設值為 FALSE。

### <a name="remarks"></a>備註

##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor

設定按鈕文字的背景色彩。

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*crFace*<br/>
[in]RGB 色彩值。

*bRedraw*<br/>
[in]若要立即; 重繪螢幕，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

使用這個方法來定義新的填滿色彩的按鈕背景 (face)。 請注意，不是背景填滿的時機[CMFCButton::m_bTransparent](#m_btransparent)成員變數為 TRUE。

##  <a name="setimage"></a>  CMFCButton::SetImage

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

*hIcon*<br/>
[in]包含點陣圖和新的映像的遮罩的圖示的控制代碼。

*bAutoDestroy*<br/>
[in]若要指定點陣圖的資源會自動; 終結，則為 TRUE否則為 FALSE。 預設值為 TRUE。

*hIconHot*<br/>
[in]包含所選的狀態影像的圖示的控制代碼。

*hBitmap*<br/>
[in]包含未選取狀態的影像之點陣圖的控制代碼。

*hBitmapHot*<br/>
[in]包含所選狀態的影像之點陣圖的控制代碼。

*uiBmpResId*<br/>
[in]非選取的映像的資源識別碼。

*uiBmpHotResId*<br/>
[in]選取的映像的資源識別碼。

*bMap3dColors*<br/>
[in]指定透明背景的色彩按鈕;也就是表面的按鈕。 若要使用的色彩值 RGB （192，192，192;），則為 TRUE若要使用所定義的色彩值，則為 FALSE `AFX_GLOBAL_DATA::clrBtnFace`。

*hIconDisabled*<br/>
[in]已停用的映像的圖示的控制代碼。

*hBitmapDisabled*<br/>
[in]包含已停用的影像之點陣圖的控制代碼。

*uiBmpDsblResID*<br/>
[in]已停用點陣圖的資源識別碼。

*bAlphaBlend*<br/>
[in]若為 true，則使用 alpha 色板; 的使用僅 32 位元映像設為 FALSE，使用只有 alpha 色頻影像。 預設值為 FALSE。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下列範例示範如何使用各種版本`SetImage`方法中的`CMFCButton`類別。 範例是一部分[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor

設定資料指標的影像。

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>參數

*hcursor*<br/>
[in]資料指標控制代碼。

### <a name="remarks"></a>備註

使用這個方法將資料指標的映像，例如手狀游標，關聯 按鈕。 資料指標會從應用程式資源載入。

### <a name="example"></a>範例

下列範例示範如何使用`SetMouseCursor`方法中的`CMFCButton`類別。 此範例是中的程式碼的一部分[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand

指針的映像中設定資料指標。

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>備註

使用這個方法與按鈕關聯的左手邊的游標影像。 資料指標會從應用程式資源載入。

##  <a name="setstdimage"></a>  CMFCButton::SetStdImage

使用`CMenuImages`物件來設定按鈕的影像。

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>參數

*id*<br/>
[in]其中一個按鈕映像識別碼中所定義`CMenuImage::IMAGES_IDS`列舉型別。 指定的映像值，例如箭號、 pin 和選項按鈕的影像。

*state*<br/>
[in]其中一個按鈕映像的狀態識別碼中所定義`CMenuImages::IMAGE_STATE`列舉型別。 映像狀態指定例如黑色、 灰色、 淺灰色，白色和暗灰色的按鈕色彩。 預設值是 `CMenuImages::ImageBlack`。

*idDisabled*<br/>
[in]其中一個按鈕映像識別碼中所定義`CMenuImage::IMAGES_IDS`列舉型別。 映像表示按鈕已停用。 預設值是第一個按鈕影像 ( `CMenuImages::IdArrowDown`)。

### <a name="remarks"></a>備註

##  <a name="settextcolor"></a>  CMFCButton::SetTextColor

設定未選取按鈕的按鈕文字的色彩。

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>參數

*clrText*<br/>
[in]RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor

設定已選取按鈕的按鈕文字的色彩。

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>參數

*clrTextHot*<br/>
[in]RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="settooltip"></a>  CMFCButton::SetTooltip

關聯 按鈕的工具提示。

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>參數

*lpszToolTipText*<br/>
[in]工具提示的文字指標。 請指定 NULL 來停用工具提示。

### <a name="remarks"></a>備註

##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent

調整大小的按鈕，以包含其按鈕文字和影像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
[in]若要計算，但不是能變更的按鈕; 新的大小，則為 TRUE若要變更按鈕的大小，則為 FALSE。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

A`CSize`物件，其中包含新按鈕的大小。

### <a name="remarks"></a>備註

根據預設，這個方法會計算新的大小，其中包含 10 個像素水平邊界和 5 個像素垂直邊界。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl 類別](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)
