---
title: CMFCButton 類別
ms.date: 08/28/2018
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
ms.openlocfilehash: 7628ac353d01c2a6853e35a35bd1f702d3bb041e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505852"
---
# <a name="cmfcbutton-class"></a>CMFCButton 類別

類別會將功能新增至 [CButton](../../mfc/reference/cbutton-class.md) 類別，例如對齊按鈕文字、結合按鈕文字和影像、選取游標和指定工具提示。`CMFCButton`

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
|[CMFCButton::CleanUp](#cleanup)|重設內部變數並釋出已配置的資源，例如影像、點陣圖和圖示。|
|`CMFCButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCButton::DrawItem`|當主控描繪按鈕的視覺外觀變更時由架構呼叫。 （覆寫[CButton：:D rawitem](../../mfc/reference/cbutton-class.md#drawitem)。）|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|指定是否要在大型工具提示視窗中顯示工具提示的完整文字，或在小型工具提示視窗中顯示文字的截斷版本。|
|[CMFCButton::EnableMenuFont](#enablemenufont)|指定按鈕文字字型是否與應用程式功能表字型相同。|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|指定按鈕框線的樣式是否對應至目前的 Windows 主題。|
|`CMFCButton::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|傳回基礎工具提示控制項的參考。|
|[CMFCButton::IsAutoCheck](#isautocheck)|指出核取方塊或選項按鈕是否為 [自動] 按鈕。|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|指出按鈕是否設定為自動重複模式。|
|[CMFCButton::IsCheckBox](#ischeckbox)|指出按鈕是否為核取方塊按鈕。|
|[CMFCButton::IsChecked](#ischecked)|指出是否已核取 [目前] 按鈕。|
|[CMFCButton::IsHighlighted](#ishighlighted)|指出是否反白顯示按鈕。|
|[CMFCButton::IsPressed](#ispressed)|指出是否已推送並反白顯示按鈕。|
|[CMFCButton::IsPushed](#ispushed)|指出是否已推送按鈕。|
|[CMFCButton::IsRadioButton](#isradiobutton)|指出按鈕是否為選項按鈕。|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|指出按鈕框線的樣式是否對應至目前的 Windows 主題。|
|`CMFCButton::OnDrawParentBackground`|在指定的區域中繪製按鈕父系的背景。 （覆寫[AFX_GLOBAL_DATA：:D rawparentbackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|會先轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)和[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|將按鈕設定為自動重複模式。|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|設定已核取按鈕的影像。|
|[CMFCButton::SetFaceColor](#setfacecolor)|設定按鈕文字的背景色彩。|
|[CMFCButton::SetImage](#setimage)|設定按鈕的影像。|
|[CMFCButton::SetMouseCursor](#setmousecursor)|設定資料指標影像。|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|將游標設定為手的影像。|
|[CMFCButton::SetStdImage](#setstdimage)|`CMenuImages`使用物件來設定按鈕影像。|
|[CMFCButton::SetTextColor](#settextcolor)|設定未選取按鈕的按鈕文字色彩。|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|設定已選取按鈕的按鈕文字色彩。|
|[CMFCButton::SetTooltip](#settooltip)|將工具提示與按鈕產生關聯。|
|[CMFCButton::SizeToContent](#sizetocontent)|調整按鈕的大小，以包含其按鈕文字和影像。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|由架構呼叫以繪製按鈕。|
|[CMFCButton::OnDrawBorder](#ondrawborder)|由架構呼叫以繪製按鈕的框線。|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|由架構呼叫以繪製按鈕的焦點矩形。|
|[CMFCButton::OnDrawText](#ondrawtext)|由架構呼叫以繪製按鈕文字。|
|[CMFCButton::OnFillBackground](#onfillbackground)|由架構呼叫以繪製按鈕文字的背景。|
|[CMFCButton::SelectFont](#selectfont)|抓取與指定的裝置內容相關聯的字型。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|指定按鈕文字的對齊方式。|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|指定是否要使用 Windows XP 主題。|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|指出是否要在按鈕周圍繪製焦點矩形。|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|指定按鈕的樣式，例如 [無邊框]、[平面]、[半平面] 或 [3D]。|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|若為 [TRUE]，則會啟用 [已停用] 按鈕繪製為灰色。|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|指示游標停留在其上時，是否要反白顯示 BS_CHECKBOX 樣式的按鈕。|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|指出是否回應按鈕向下事件。|
|[CMFCButton::m_bRightImage](#m_brightimage)|指出是否要在按鈕的右側顯示影像。|
|[CMFCButton::m_bTopImage](#m_bTopImage)| 指出影像是否在按鈕上方。|
|[CMFCButton::m_bTransparent](#m_btransparent)|指出按鈕是否為透明。|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| 指出是否按一下最後一個 click 事件。|

## <a name="remarks"></a>備註

其他類型的按鈕是衍生自`CMFCButton`類別，例如支援超連結的[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)類別，以及支援 [ `CMFCColorButton`色彩選擇器] 對話方塊的類別。

`CMFCButton`物件的樣式可以是*3d*、*平面*、*半平面*或*無框線*。 按鈕文字可以在按鈕的左側、頂端或中央對齊。 在執行時間，您可以控制按鈕是否顯示文字、影像或文字和影像。 您也可以指定在游標停留在按鈕上時，顯示特定的游標影像。

直接在程式碼中建立按鈕控制項，或使用**MFC 類別的 Wizard** tool 和對話方塊範本。 如果您直接建立按鈕控制項，請將`CMFCButton`變數加入至應用程式，然後呼叫`CMFCButton`物件的函式`Create`和方法。 如果您使用**MFC 類別 Wizard**，請將`CButton`變數加入至您的應用程式，然後將變數的類型從`CButton`變更為`CMFCButton`。

若要處理對話方塊應用程式中的通知訊息，請針對每個通知加入訊息對應專案和事件處理常式。 `CMFCButton`物件所傳送的通知與`CButton`物件所傳送的通知相同。

## <a name="example"></a>範例

下列範例示範如何使用`CMFCButton`類別中的各種方法來設定按鈕的屬性。 此範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

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

**標頭：** afxbutton。h

##  <a name="cleanup"></a>CMFCButton：：清除

重設內部變數並釋出已配置的資源，例如影像、點陣圖和圖示。

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip

指定是否要在大型工具提示視窗中顯示工具提示的完整文字，或在小型工具提示視窗中顯示文字的截斷版本。

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
在TRUE 表示顯示所有文字;FALSE 表示顯示截斷的文字。

### <a name="remarks"></a>備註

##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont

指定按鈕文字字型是否與應用程式功能表字型相同。

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
在TRUE 表示使用應用程式功能表字型作為按鈕文字字型;FALSE 表示使用系統字型。 預設值為 TRUE。

*bRedraw*<br/>
在TRUE 表示立即重繪螢幕;否則為 FALSE。 預設值為 TRUE。

### <a name="remarks"></a>備註

如果您未使用這個方法來指定按鈕文字字型，您可以使用[CWnd：： SetFont](../../mfc/reference/cwnd-class.md#setfont)方法來指定字型。 如果您沒有指定字型，此架構會設定預設字型。

##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

指定按鈕框線的樣式是否對應至目前的 Windows 主題。

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
在TRUE 表示使用目前的 Windows 主題繪製按鈕框線;FALSE 表示不使用 Windows 主題。 預設值為 TRUE。

### <a name="remarks"></a>備註

這個方法會影響您的應用程式中衍生自類別的`CMFCButton`所有按鈕。

##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl

傳回基礎工具提示控制項的參考。

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>傳回值

基礎工具提示控制項的參考。

### <a name="remarks"></a>備註

##  <a name="isautocheck"></a>CMFCButton::IsAutoCheck

指出核取方塊或選項按鈕是否為 [自動] 按鈕。

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>傳回值

如果按鈕的樣式為 BS_AUTOCHECKBOX 或 BS_AUTORADIOBUTTON，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

指出按鈕是否設定為自動重複模式。

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>傳回值

如果按鈕設定為自動重複模式，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

使用[CMFCButton：： SetAutorepeatMode](#setautorepeatmode)方法，將按鈕設定為自動重複模式。

##  <a name="ischeckbox"></a>CMFCButton::IsCheckBox

指出按鈕是否為核取方塊按鈕。

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>傳回值

如果按鈕有 BS_CHECKBOX 或 BS_AUTOCHECKBOX 樣式，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="ischecked"></a>CMFCButton：： IsChecked

指出是否已核取 [目前] 按鈕。

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>傳回值

如果目前的按鈕已核取，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

架構使用不同的方式來表示已檢查不同種類的按鈕。 例如，當選項按鈕包含點時，就會進行檢查。當包含**X**時，會檢查核取方塊。

##  <a name="ishighlighted"></a>CMFCButton::IsHighlighted

指出是否反白顯示按鈕。

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>傳回值

如果按鈕已反白顯示，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當滑鼠停留在按鈕上時，按鈕會反白顯示。

##  <a name="ispressed"></a>CMFCButton::IsPressed

指出是否已推送並反白顯示按鈕。

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>傳回值

如果按鈕已按下，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="ispushed"></a>CMFCButton::IsPushed

指出是否已推送按鈕。

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>傳回值

如果按鈕已推送，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="isradiobutton"></a>CMFCButton::IsRadioButton

指出按鈕是否為選項按鈕。

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕樣式為 BS_RADIOBUTTON 或 BS_AUTORADIOBUTTON，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

指出按鈕框線的樣式是否對應至目前的 Windows 主題。

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>傳回值

如果按鈕框線的樣式對應至目前的 Windows 主題，則為 TRUE;否則為 FALSE。

## <a name="a-namem_bdontusewinxptheme-cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

指定是否要在繪製按鈕時使用 Windows XP 主題。

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus

指出是否要在按鈕周圍繪製焦點矩形。

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>備註

`m_bDrawFocus`將成員設定為 TRUE，以指定當按鈕收到焦點時，架構會在按鈕的文字和影像周圍繪製焦點矩形。

此`CMFCButton`函式會將此成員初始化為 TRUE。

##  <a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

若為 [TRUE]，則會啟用 [已停用] 按鈕繪製為灰色。

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

指示游標停留在其上時，是否要反白顯示 BS_CHECKBOX 樣式的按鈕。

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>備註

`m_bHighlightChecked`將成員設定為 TRUE，指定當滑鼠停留在 BS_CHECKBOX 樣式的按鈕上方時，該架構會反白顯示。

##  <a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

指出是否回應按鈕向下事件。

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>CMFCButton::m_bRightImage

指出是否要在按鈕的右側顯示影像。

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)

指出影像是否在按鈕上方。

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>備註

`m_bRightImage`將成員設定為 TRUE，指定架構將會在按鈕的文字標籤右邊顯示按鈕的影像。

##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent

指出按鈕是否為透明。

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>備註

`m_bTransparent`將成員設定為 TRUE，指定架構會使按鈕變成透明。 此`CMFCButton`函式會將此成員初始化為 FALSE。

##  <a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

指定按鈕文字的對齊方式。

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>備註

使用下列`CMFCButton::AlignStyle`其中一個列舉值來指定按鈕文字的對齊方式：

|值|描述|
|-----------|-----------------|
|ALIGN_CENTER|預設將按鈕文字對齊按鈕的中心。|
|ALIGN_LEFT|將按鈕文字對齊按鈕的左邊。|
|ALIGN_RIGHT|將按鈕文字對齊按鈕的右側。|

此`CMFCButton`函式會將這個成員初始化為 ALIGN_CENTER。

##  <a name="m_bWasDblClk"></a>CMFCButton：： m_bWasDblClk] （#m_bWasDblClk） |

指出最後按一下事件是否為按兩下。 |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle

指定按鈕的樣式，例如 [無邊框]、[平面]、[半平面] 或 [3D]。

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>備註

下表列出`CMFCButton::m_nFlatStyle`指定按鈕外觀的列舉值。

|值|描述|
|-----------|-----------------|
|BUTTONSTYLE_3D|預設按鈕看起來有高、三維邊。 按一下按鈕時，按鈕看起來會被按下深度縮排。|
|BUTTONSTYLE_FLAT|當滑鼠未停留在按鈕上時，按鈕看起來會是二維，而且不會有凸起的邊。 當滑鼠停留在按鈕上時，按鈕會顯示為具有 low、三維邊。 按一下按鈕時，按鈕會顯示為按下淺縮排。|
|BUTTONSTYLE_SEMIFLAT|按鈕看起來會有較低的三維邊。 按一下按鈕時，按鈕看起來會被按下深度縮排。|
|BUTTONSTYLE_NOBORDERS|按鈕沒有凸起的邊，而且一律會顯示為二維。 按一下按鈕時，它看起來不會按下縮排。|

此`CMFCButton`函式會將這個成員初始化為 BUTTONSTYLE_3D。

### <a name="example"></a>範例

下列範例示範如何`m_nFlatStyle` `CMFCButton`在類別中設定成員變數的值。 這個範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

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
在裝置內容的指標。

*rect*<br/>
在矩形的參考，其為按鈕的界限。

*uiState*<br/>
在目前的按鈕狀態。 如需詳細資訊，請`itemState`參閱[DRAWITEMSTRUCT 結構](/windows/win32/api/winuser/ns-winuser-drawitemstruct)的成員主題。

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
在裝置內容的指標。

*rectClient*<br/>
在矩形的參考，其為按鈕的界限。

*uiState*<br/>
在目前的按鈕狀態。 如需詳細資訊，請`itemState`參閱[DRAWITEMSTRUCT 結構](/windows/win32/api/winuser/ns-winuser-drawitemstruct)的成員主題。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼來繪製框線。

##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect

由架構呼叫以繪製按鈕的焦點矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*rectClient*<br/>
在矩形的參考，其為按鈕的界限。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼來繪製焦點矩形。

##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText

由架構呼叫以繪製按鈕文字。

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
在裝置內容的指標。

*rect*<br/>
在矩形的參考，其為按鈕的界限。

*strText*<br/>
在要繪製的文字。

*uiDTFlags*<br/>
在指定如何格式化文字的旗標。 如需詳細資訊，請參閱[CDC：:D rawtext](../../mfc/reference/cdc-class.md#drawtext)方法的*nFormat*參數。

*uiState*<br/>
[in] 保留。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼來繪製按鈕文字。

##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground

由架構呼叫以繪製按鈕文字的背景。

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*rectClient*<br/>
在矩形的參考，其為按鈕的界限。

### <a name="remarks"></a>備註

覆寫這個方法，以使用您自己的程式碼來繪製按鈕的背景。

##  <a name="selectfont"></a>  CMFCButton::SelectFont

抓取與指定的裝置內容相關聯的字型。

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

### <a name="return-value"></a>傳回值

覆寫這個方法，以使用您自己的程式碼來抓取字型。

### <a name="remarks"></a>備註

##  <a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

將按鈕設定為自動重複模式。

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>參數

*nTimeDelay*<br/>
在非負數值，指定傳送至父視窗的訊息之間的間隔。 間隔是以毫秒為單位，其預設值為500毫秒。 指定零可停用自動重複訊息模式。

### <a name="remarks"></a>備註

這個方法會讓按鈕持續傳送 WM_COMMAND 訊息到父視窗，直到放開按鈕，或將*nTimeDelay*參數設定為零。

##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage

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

*hIcon*<br/>
在圖示的控制碼，其中包含新影像的點陣圖和遮罩。

*bAutoDestroy*<br/>
在TRUE 表示要自動終結點陣圖資源;否則為 FALSE。 預設值為 TRUE。

*hIconHot*<br/>
在圖示的控制碼，其中包含所選取狀態的影像。

*hBitmap*<br/>
在包含非選取狀態影像之點陣圖的控制碼。

*hBitmapHot*<br/>
在點陣圖的控制碼，其中包含所選取狀態的影像。

*bMap3dColors*<br/>
在指定按鈕背景的透明色彩;也就是按鈕的臉部。 TRUE 表示使用 RGB （192，192，192）的色彩值;FALSE 表示使用定義`AFX_GLOBAL_DATA::clrBtnFace`的色彩值。

*uiBmpResId*<br/>
在非選取之映射的資源識別碼。

*uiBmpHotResId*<br/>
在所選映射的資源識別碼。

*hIconDisabled*<br/>
在已停用影像之圖示的控制碼。

*hBitmapDisabled*<br/>
在包含已停用影像之點陣圖的控制碼。

*uiBmpDsblResID*<br/>
在已停用點陣圖的資源識別碼。

*bAlphaBlend*<br/>
在TRUE 表示只使用使用 Alpha 色板的32位影像;FALSE，表示不只使用 Alpha 聲道影像。 預設值為 FALSE。

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
在RGB 色彩值。

*bRedraw*<br/>
在TRUE 表示立即重繪螢幕;否則為 FALSE。

### <a name="remarks"></a>備註

使用此方法可為按鈕背景（臉部）定義新的填滿色彩。 請注意，當[CMFCButton：： m_bTransparent](#m_btransparent)成員變數為 TRUE 時，背景不會填滿。

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

*hIcon*<br/>
在圖示的控制碼，其中包含新影像的點陣圖和遮罩。

*bAutoDestroy*<br/>
在TRUE 表示要自動終結點陣圖資源;否則為 FALSE。 預設值為 TRUE。

*hIconHot*<br/>
在圖示的控制碼，其中包含所選取狀態的影像。

*hBitmap*<br/>
在包含非選取狀態影像之點陣圖的控制碼。

*hBitmapHot*<br/>
在點陣圖的控制碼，其中包含所選取狀態的影像。

*uiBmpResId*<br/>
在非選取之映射的資源識別碼。

*uiBmpHotResId*<br/>
在所選映射的資源識別碼。

*bMap3dColors*<br/>
在指定按鈕背景的透明色彩;也就是按鈕的臉部。 TRUE 表示使用 RGB （192，192，192）的色彩值;FALSE 表示使用定義`AFX_GLOBAL_DATA::clrBtnFace`的色彩值。

*hIconDisabled*<br/>
在已停用影像之圖示的控制碼。

*hBitmapDisabled*<br/>
在包含已停用影像之點陣圖的控制碼。

*uiBmpDsblResID*<br/>
在已停用點陣圖的資源識別碼。

*bAlphaBlend*<br/>
在TRUE 表示只使用使用 Alpha 色板的32位影像;FALSE，表示不只使用 Alpha 聲道影像。 預設值為 FALSE。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下列範例示範如何`SetImage` `CMFCButton`在類別中使用各種版本的方法。 此範例是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>CMFCButton::SetMouseCursor

設定資料指標影像。

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>參數

*hcursor*<br/>
在資料指標的控制碼。

### <a name="remarks"></a>備註

使用此方法可將游標影像（例如手形游標）與按鈕產生關聯。 資料指標是從應用程式資源載入。

### <a name="example"></a>範例

下列範例示範如何`SetMouseCursor` `CMFCButton`在類別中使用方法。 此範例是[新控制項範例](../../overview/visual-cpp-samples.md)中程式碼的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

將游標設定為手的影像。

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>備註

使用此方法可將手的游標影像與按鈕產生關聯。 資料指標是從應用程式資源載入。

##  <a name="setstdimage"></a>CMFCButton::SetStdImage

`CMenuImages`使用物件來設定按鈕影像。

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>參數

*id*<br/>
在`CMenuImage::IMAGES_IDS`列舉中所定義的其中一個按鈕影像識別碼。 影像值會指定影像，例如箭號、釘選和選項按鈕。

*state*<br/>
在`CMenuImages::IMAGE_STATE`列舉中所定義的其中一個按鈕影像狀態識別碼。 影像狀態會指定按鈕色彩，例如黑色、灰色、淺灰色、白色和暗灰色。 預設值為 `CMenuImages::ImageBlack`。

*idDisabled*<br/>
在`CMenuImage::IMAGES_IDS`列舉中所定義的其中一個按鈕影像識別碼。 影像表示按鈕已停用。 預設值為第一個按鈕影像（ `CMenuImages::IdArrowDown`）。

### <a name="remarks"></a>備註

##  <a name="settextcolor"></a>CMFCButton::SetTextColor

設定未選取按鈕的按鈕文字色彩。

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>參數

*clrText*<br/>
在RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

設定已選取按鈕的按鈕文字色彩。

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>參數

*clrTextHot*<br/>
在RGB 色彩值。

### <a name="remarks"></a>備註

##  <a name="settooltip"></a>CMFCButton::SetTooltip

將工具提示與按鈕產生關聯。

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>參數

*lpszToolTipText*<br/>
在工具提示文字的指標。 指定 Null 可停用工具提示。

### <a name="remarks"></a>備註

##  <a name="sizetocontent"></a>CMFCButton：： System.windows.window.sizetocontent

調整按鈕的大小，以包含其按鈕文字和影像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
在TRUE 表示計算（但不變更）按鈕的新大小;FALSE 可變更按鈕的大小。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

`CSize`物件，其中包含按鈕的新大小。

### <a name="remarks"></a>備註

根據預設，這個方法會計算新的大小，其中包含10圖元的水準邊界和5圖元的垂直邊界。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl 類別](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)
