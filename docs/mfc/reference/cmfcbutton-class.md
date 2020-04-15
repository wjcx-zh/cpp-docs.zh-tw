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
ms.openlocfilehash: 5434801969a55387a5b5555c9a4ade22f1969e7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367782"
---
# <a name="cmfcbutton-class"></a>CMFCButton 類別

該`CMFCButton`類向[CButton](../../mfc/reference/cbutton-class.md)類添加功能,例如對齊按鈕文本、組合按鈕文本和圖像、選擇游標以及指定工具提示。

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
|[CMFC按鈕::清理](#cleanup)|重置內部變數並釋放分配的資源,如圖像、位圖和圖示。|
|`CMFCButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|`CMFCButton::DrawItem`|當所有者繪製按鈕的可視方面已更改時,由框架調用。 (覆蓋[CButton::D原始專案](../../mfc/reference/cbutton-class.md#drawitem)))|
|[CMFC按鈕::啟用全文字工具提示](#enablefulltexttooltip)|指定是在大型工具提示視窗中顯示工具提示的全文,還是在小型工具提示視窗中顯示文本的截斷版本。|
|[CMFC按鈕::啟用選單字型](#enablemenufont)|指定按鈕文字字體是否與應用程式功能表字體相同。|
|[CMFC按鈕::啟用WindowsTheming](#enablewindowstheming)|指定按鈕邊框的樣式是否與當前 Windows 主題相對應。|
|`CMFCButton::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|[CMFC按鈕::取得工具提示](#gettooltipctrl)|返回對基礎工具提示控件的引用。|
|[CMFC按鈕::自動檢查](#isautocheck)|指示複選框或單選按鈕是自動按鈕。|
|[CMFC按鈕::自動重複命令模式](#isautorepeatcommandmode)|指示按鈕是否已設置為自動重複模式。|
|[CMFC按鈕::是支票盒](#ischeckbox)|指示按鈕是否為複選框按鈕。|
|[CMFC按鈕::已選中](#ischecked)|指示是否選擇當前按鈕。|
|[CMFC按鈕::已突出顯示](#ishighlighted)|指示按鈕是否突出顯示。|
|[CMFC按鈕::按壓](#ispressed)|指示是否按下並突出顯示按鈕。|
|[CMFC按鈕:按壓](#ispushed)|指示是否按下按鈕。|
|[CMFC按鈕::是無線按鈕](#isradiobutton)|指示按鈕是否為單選按鈕。|
|[CMFC按鈕:Windows啟用](#iswindowsthemingenabled)|指示按鈕邊框的樣式是否與當前 Windows 主題相對應。|
|`CMFCButton::OnDrawParentBackground`|在指定區域中繪製按鈕父級的背景。 (覆蓋[AFX_GLOBAL_DATA::D原始父背景](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|在視窗訊息發送到[翻譯訊息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[調度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)視窗功能之前進行翻譯。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|
|[CMFC按鈕::設定自動重複模式](#setautorepeatmode)|將按鈕設置為自動重複模式。|
|[CMFC按鈕::設定已檢查影像](#setcheckedimage)|設置選中按鈕的圖像。|
|[CMFC按鈕::設置臉彩](#setfacecolor)|設置按鈕文字的背景顏色。|
|[CMFC按鈕::設定影像](#setimage)|設置按鈕的圖像。|
|[CMFC按鈕::設定滑鼠游標](#setmousecursor)|設置游標圖像。|
|[CMFC按鈕::設定滑鼠游標手](#setmousecursorhand)|將游標設置到手的圖像。|
|[CMFC按鈕::設定StdImage](#setstdimage)|使用物件`CMenuImages`設置按鈕圖像。|
|[CMFC按鈕::設定文字顏色](#settextcolor)|設定未選擇的按鈕的按鈕文字的顏色。|
|[CMFC按鈕::設定文字熱色](#settexthotcolor)|設置所選按鈕的按鈕文字的顏色。|
|[CMFC按鈕::設定工具提示](#settooltip)|將工具提示與按鈕關聯。|
|[CMFC按鈕::大小到內容](#sizetocontent)|調整按鈕的大小以包含其按鈕文本和圖像。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC按鈕:在畫上](#ondraw)|由框架調用以繪製一個按鈕。|
|[CMFC按鈕::在繪製邊框](#ondrawborder)|由框架調用以繪製按鈕的邊框。|
|[CMFC按鈕::在Draw焦點上](#ondrawfocusrect)|框架調用以繪製按鈕的焦點矩形。|
|[CMFC按鈕::畫中文字](#ondrawtext)|由框架調用以繪製按鈕文本。|
|[CMFC按鈕::打開填充背景](#onfillbackground)|由框架調用以繪製按鈕文本的背景。|
|[CMFC按鈕::選擇字型](#selectfont)|檢索與指定設備上下文關聯的字體。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC按鈕::m_nAlignStyle](#m_nalignstyle)|指定按鈕文字的對齊方式。|
|[CMFC按鈕:m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|指定是否使用 Windows XP 主題。|
|[CMFC按鈕:m_bDrawFocus](#m_bdrawfocus)|指示是否圍繞按鈕繪製焦點矩形。|
|[CMFC按鈕::m_nFlatStyle](#m_nflatstyle)|指定按鈕的樣式,如無邊框、平面、半平面或 3D。|
|[CMFC按鈕::m_bGrayDisabled](#m_bGrayDisabled)|當 TRUE 時,使禁用的按鈕繪製為灰顯。|
|[CMFC按鈕:m_bHighlightChecked](#m_bhighlightchecked)|指示游標懸停在按鈕上時是否突出顯示BS_CHECKBOX式按鈕。|
|[CMFC按鈕:m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|指示是否回應按鈕向下事件。|
|[CMFC按鈕:m_bRightImage](#m_brightimage)|指示是否在按鈕右側顯示圖像。|
|[CMFC按鈕:m_bTopImage](#m_bTopImage)| 指示圖像是否位於按鈕頂部。|
|[CMFC按鈕::m_bTransparent](#m_btransparent)|指示按鈕是否透明。|
|[CMFC按鈕:m_bWasDblClk](#m_bWasDblClk)| 指示最後一次單擊事件是否為按兩下。|

## <a name="remarks"></a>備註

其他類型的按鈕派生自`CMFCButton`類,例如支援超連結的[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)類和支援顏色選取器對話`CMFCColorButton`方塊的 類。

`CMFCButton`物件的樣式可以是*3D,**平面*,*半平面*或*無邊框*。 按鈕文字可以在按鈕的左側、頂部或中心對齊。 在執行時,您可以控制按鈕是顯示文本、圖像還是文本和圖像。 還可以指定在游標懸停在按鈕上時顯示特定的游標圖像。

直接在代碼中創建按鈕控制項,或使用**MFC 類嚮導**工具和對話方塊樣本建立按鈕控制項。 如果直接創建按鈕控制項,請向應用程式添加`CMFCButton`變數,然後調用`Create``CMFCButton`物件的建構函數和方法。 如果使用**MFC 類別精靈**,請`CButton`向應用程式新增變數,然後將變數的類型從`CButton`變更為`CMFCButton`。

要處理對話框應用程式中的通知消息,請為每個通知添加消息映射條目和事件處理程式。 `CMFCButton`物件發送的通知與`CButton`物件發送的通知相同。

## <a name="example"></a>範例

下面的範例展示如何使用`CMFCButton`類中的各種方法配置按鈕的屬性。 該示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afx按鈕.h

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a>CMFC按鈕::清理

重置內部變數並釋放分配的資源,如圖像、位圖和圖示。

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a>CMFC按鈕::啟用全文字工具提示

指定是在大型工具提示視窗中顯示工具提示的全文,還是在小型工具提示視窗中顯示文本的截斷版本。

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>參數

*邦*<br/>
[在]TRUE 以顯示所有文本;FALSE 以顯示截斷的文本。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a>CMFC按鈕::啟用選單字型

指定按鈕文字字體是否與應用程式功能表字體相同。

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*邦*<br/>
[在]TRUE 使用應用程式功能表字體作為按鈕文字字體;FALSE 以使用系統字體。 預設值是 TRUE。

*bredraw*<br/>
[在]TRUE 可立即重繪螢幕;否則,FALSE。 預設值是 TRUE。

### <a name="remarks"></a>備註

如果不使用此方法指定按鈕文本字體,則可以使用[CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont)方法指定字體。 如果根本不指定字體,則框架將設置預設字體。

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a>CMFC按鈕::啟用WindowsTheming

指定按鈕邊框的樣式是否與當前 Windows 主題相對應。

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 使用目前的 Windows 主題繪製按鈕邊框;FALSE 不使用 Windows 主題。 預設值是 TRUE。

### <a name="remarks"></a>備註

此方法會影響應用程式中派生自`CMFCButton`類的所有按鈕。

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a>CMFC按鈕::取得工具提示

返回對基礎工具提示控件的引用。

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>傳回值

對基礎工具提示控件的引用。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a>CMFC按鈕::自動檢查

指示複選框或單選按鈕是自動按鈕。

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>傳回值

如果按鈕具有樣式BS_AUTOCHECKBOX或BS_AUTORADIOBUTTON,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a>CMFC按鈕::自動重複命令模式

指示按鈕是否已設置為自動重複模式。

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>傳回值

如果按鈕設置為自動重複模式,則為 TRUE;如果按鈕設置為自動重複模式,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

使用[CMFCButton::設定自動重複模式](#setautorepeatmode)方法將按鈕設置為自動重複模式。

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a>CMFC按鈕::是支票盒

指示按鈕是否為複選框按鈕。

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>傳回值

如果按鈕具有BS_CHECKBOX或BS_AUTOCHECKBOX樣式,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a>CMFC按鈕::已選中

指示是否選擇當前按鈕。

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>傳回值

如果選中當前按鈕,則為 TRUE;如果選中當前按鈕,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

框架使用不同的方法來指示檢查不同類型的按鈕。 例如,當單選按鈕包含點時,將選中它;當複選框包含**X**時,將選中它。

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a>CMFC按鈕::已突出顯示

指示按鈕是否突出顯示。

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>傳回值

如果按鈕突出顯示,則為 TRUE;如果按鈕突出顯示,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

當滑鼠懸停在按鈕上時,按鈕將突出顯示。

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a>CMFC按鈕::按壓

指示是否按下並突出顯示按鈕。

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>傳回值

如果按下按鈕,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a>CMFC按鈕:按壓

指示是否按下按鈕。

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>傳回值

如果按下按鈕,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a>CMFC按鈕::是無線按鈕

指示按鈕是否為單選按鈕。

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>傳回值

如果按鈕樣式為BS_RADIOBUTTON或BS_AUTORADIOBUTTON,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a>CMFC按鈕:Windows啟用

指示按鈕邊框的樣式是否與當前 Windows 主題相對應。

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>傳回值

如果按鈕邊框的樣式對應於當前 Windows 主題,則為 TRUE;否則,FALSE。

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFC按鈕:m_bDontUseWinXPTheme

指定在繪製按鈕時是否使用 Windows XP 主題。

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a>CMFC按鈕:m_bDrawFocus

指示是否圍繞按鈕繪製焦點矩形。

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>備註

將`m_bDrawFocus`成員設定為 TRUE 以指定如果按鈕接收焦點,框架將在按鈕的文本和圖像周圍繪製焦點矩形。

建構`CMFCButton`函數將此成員初始化為 TRUE。

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a>CMFC按鈕::m_bGrayDisabled

當 TRUE 時,使禁用的按鈕繪製為灰顯。

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a>CMFC按鈕:m_bHighlightChecked

指示游標懸停在按鈕上時是否突出顯示BS_CHECKBOX式按鈕。

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>備註

將`m_bHighlightChecked`成員設置為 TRUE 以指定當滑鼠懸停在按鈕上時,框架將突出顯示BS_CHECKBOX式按鈕。

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a>CMFC按鈕:m_bResponseOnButtonDown

指示是否回應按鈕向下事件。

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a>CMFC按鈕:m_bRightImage

指示是否在按鈕右側顯示圖像。

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a>CMFC按鈕::m_bTopImage*(#m_bTopImage)

指示圖像是否位於按鈕頂部。

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>備註

將`m_bRightImage`成員設定為 TRUE 以指定框架將在按鈕的文本標籤右側顯示按鈕的圖像。

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a>CMFC按鈕::m_bTransparent

指示按鈕是否透明。

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>備註

將`m_bTransparent`成員設定為 TRUE 以指定框架將使按鈕透明。 建構`CMFCButton`函數將此成員初始化到 FALSE。

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a>CMFC按鈕::m_nAlignStyle

指定按鈕文字的對齊方式。

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>備註

使用以下`CMFCButton::AlignStyle`的手舉值之一指定按鈕文字的對齊方式:

|值|描述|
|-----------|-----------------|
|ALIGN_CENTER|( 預設 )將按鈕文字對齊到按鈕的中心。|
|ALIGN_LEFT|將按鈕文字對齊到按鈕的左側。|
|ALIGN_RIGHT|將按鈕文字對齊到按鈕的右側。|

建構`CMFCButton`函數將此成員初始化到ALIGN_CENTER。

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a>CMFC按鈕::m_bWasDblClk*(#m_bWasDblClk)*

指示上次按一下事件是否為按兩下。

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a>CMFC按鈕::m_nFlatStyle

指定按鈕的樣式,如無邊框、平面、半平面或 3D。

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>備註

下表列出了`CMFCButton::m_nFlatStyle`指定按鈕外觀的枚舉值。

|值|描述|
|-----------|-----------------|
|BUTTONSTYLE_3D|( 預設 )按鈕似乎有高的三維邊。 按下該按鈕時,該按鈕似乎被壓入深縮進。|
|BUTTONSTYLE_FLAT|當滑鼠未在按鈕上暫停時,該按鈕顯示為二維,並且沒有凸起的邊。 當滑鼠懸停在按鈕上時,按鈕似乎有低的三維邊。 按下該按鈕時,該按鈕似乎被壓入淺縮進。|
|BUTTONSTYLE_SEMIFLAT|按鈕似乎有低的三維邊。 按下該按鈕時,該按鈕似乎被壓入深縮進。|
|BUTTONSTYLE_NOBORDERS|按鈕沒有凸起的邊,並且始終顯示為二維。 按下按鈕時,按鈕似乎不會按入縮進。|

建構`CMFCButton`函數將此成員初始化到BUTTONSTYLE_3D。

### <a name="example"></a>範例

下面的範例展示如何在`m_nFlatStyle``CMFCButton`類中設置成員變數的值。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a>CMFC按鈕:在畫上

由框架調用以繪製一個按鈕。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]對綁定按鈕的矩形的引用。

*uiState*<br/>
[在]當前按鈕狀態。 有關詳細資訊,請參閱`itemState`[DRAWITEMSTRUCT 結構](/windows/win32/api/winuser/ns-winuser-drawitemstruct)主題的成員。

### <a name="remarks"></a>備註

重寫此方法以使用您自己的代碼繪製按鈕。

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a>CMFC按鈕::在繪製邊框

由框架調用以繪製按鈕的邊框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*rectClient*<br/>
[在]對綁定按鈕的矩形的引用。

*uiState*<br/>
[在]當前按鈕狀態。 有關詳細資訊,請參閱`itemState`[DRAWITEMSTRUCT 結構](/windows/win32/api/winuser/ns-winuser-drawitemstruct)主題的成員。

### <a name="remarks"></a>備註

重寫此方法以使用您自己的代碼繪製邊框。

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFC按鈕::在Draw焦點上

框架調用以繪製按鈕的焦點矩形。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*rectClient*<br/>
[在]對綁定按鈕的矩形的引用。

### <a name="remarks"></a>備註

重寫此方法以使用自己的代碼繪製焦點矩形。

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a>CMFC按鈕::畫中文字

由框架調用以繪製按鈕文本。

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
[在]指向設備上下文的指標。

*矩形*<br/>
[在]對綁定按鈕的矩形的引用。

*斯特文字*<br/>
[在]要繪製的文本。

*uiDTFlags*<br/>
[在]指定如何設定文字格式的標誌。 有關詳細資訊,請參閱[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)方法的*nFormat*參數。

*uiState*<br/>
[in] 保留。

### <a name="remarks"></a>備註

重寫此方法以使用您自己的代碼繪製按鈕文本。

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a>CMFC按鈕::打開填充背景

由框架調用以繪製按鈕文本的背景。

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*rectClient*<br/>
[在]對綁定按鈕的矩形的引用。

### <a name="remarks"></a>備註

重寫此方法以使用您自己的代碼繪製按鈕的背景。

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a>CMFC按鈕::選擇字型

檢索與指定設備上下文關聯的字體。

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

### <a name="return-value"></a>傳回值

重寫此方法以使用您自己的代碼來檢索字型。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a>CMFC按鈕::設定自動重複模式

將按鈕設置為自動重複模式。

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>參數

*n時間延遲*<br/>
[在]指定傳送到父視窗的消息之間的間隔的非負數。 間隔以毫秒為單位測量,其預設值為 500 毫秒。 指定零以禁用自動重複消息模式。

### <a name="remarks"></a>備註

此方法使按鈕不斷向父視窗發送WM_COMMAND消息,直到釋放按鈕或*nTimeDelay*參數設置為零。

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a>CMFC按鈕::設定已檢查影像

設置選中按鈕的圖像。

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
[在]處理包含新圖像的位圖和蒙版的圖示。

*bAuto銷毀*<br/>
[在]TRUE 指定自動銷毀位圖資源;否則,FALSE。 預設值是 TRUE。

*hIconHot*<br/>
[在]處理包含所選狀態的圖像的圖示。

*hBitmap*<br/>
[在]處理包含非選定狀態圖像的點陣圖。

*hBitmapHot*<br/>
[在]處理包含所選狀態的圖像的點陣圖。

*bMap3d 顏色*<br/>
[在]為按鈕背景指定透明顏色;就是按鈕的臉。 TRUE 使用顏色值 RGB(192、192、192);FALSE 使用`AFX_GLOBAL_DATA::clrBtnFace`定義的顏色值。

*烏布佈雷西德*<br/>
[在]未選擇影像的資源 ID。

*烏布霍特雷西德*<br/>
[在]所選圖像的資源 ID。

*hIcon 已關閉*<br/>
[在]處理禁用圖像的圖示。

*hBitmap 已關閉*<br/>
[在]處理包含禁用圖像的點陣圖。

*uiBmpDsblResID*<br/>
[在]已禁用點陣圖的資源 ID。

*b阿爾法布林*<br/>
[在]TRUE 僅使用使用 alpha 通道的 32 位元影像;FALSE,不要只使用 Alpha 通道圖像。 預設值為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a>CMFC按鈕::設置臉彩

設置按鈕文字的背景顏色。

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*crFace*<br/>
[在]RGB 顏色值。

*bredraw*<br/>
[在]TRUE 立即重繪螢幕;否則,FALSE。

### <a name="remarks"></a>備註

使用此方法為按鈕背景(面)定義新的填充顏色。 請注意,當[CMFCButton::m_bTransparent](#m_btransparent)成員變數為 TRUE 時,不會填充背景。

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a>CMFC按鈕::設定影像

設置按鈕的圖像。

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
[在]處理包含新圖像的位圖和蒙版的圖示。

*bAuto銷毀*<br/>
[在]TRUE 指定自動銷毀位圖資源;否則,FALSE。 預設值是 TRUE。

*hIconHot*<br/>
[在]處理包含所選狀態的圖像的圖示。

*hBitmap*<br/>
[在]處理包含非選定狀態圖像的點陣圖。

*hBitmapHot*<br/>
[在]處理包含所選狀態的圖像的點陣圖。

*烏布佈雷西德*<br/>
[在]未選擇影像的資源 ID。

*烏布霍特雷西德*<br/>
[在]所選圖像的資源 ID。

*bMap3d 顏色*<br/>
[在]為按鈕背景指定透明顏色;就是按鈕的臉。 TRUE 使用顏色值 RGB(192、192、192);FALSE 使用`AFX_GLOBAL_DATA::clrBtnFace`定義的顏色值。

*hIcon 已關閉*<br/>
[在]處理禁用圖像的圖示。

*hBitmap 已關閉*<br/>
[在]處理包含禁用圖像的點陣圖。

*uiBmpDsblResID*<br/>
[在]已禁用點陣圖的資源 ID。

*b阿爾法布林*<br/>
[在]TRUE 僅使用使用 alpha 通道的 32 位元影像;FALSE,不要只使用 Alpha 通道圖像。 預設值為 FALSE。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下面的範例展示如何在`SetImage``CMFCButton`類中使用方法的各種版本。 該示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a>CMFC按鈕::設定滑鼠游標

設置游標圖像。

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>參數

*赫游標*<br/>
[在]游標的句柄。

### <a name="remarks"></a>備註

使用此方法將游標圖像(如手游標)與按鈕相關聯。 游標從應用程式資源載入。

### <a name="example"></a>範例

下面的示例演示如何在`SetMouseCursor``CMFCButton`類中使用 方法。 該示例是[「新建控制件」範例中的](../../overview/visual-cpp-samples.md)程式碼的一部分。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a>CMFC按鈕::設定滑鼠游標手

將游標設置到手的圖像。

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>備註

使用此方法將手的游標圖像與按鈕相關聯。 游標從應用程式資源載入。

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a>CMFC按鈕::設定StdImage

使用物件`CMenuImages`設置按鈕圖像。

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>參數

*id*<br/>
[在]列舉中定義的按鈕影像識別碼之一`CMenuImage::IMAGES_IDS`。 圖像值指定圖像,如箭頭、引腳和單選按鈕。

*state*<br/>
[在]列舉中定義的按鈕影像狀態識別碼之一`CMenuImages::IMAGE_STATE`。 圖像狀態指定按鈕顏色,如黑色、灰色、淺灰色、白色和深灰色。 預設值是 `CMenuImages::ImageBlack`。

*ID 已關閉*<br/>
[在]列舉中定義的按鈕影像識別碼之一`CMenuImage::IMAGES_IDS`。 該圖像指示按鈕已禁用。 預設值是第一個按鈕影像`CMenuImages::IdArrowDown`( 。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a>CMFC按鈕::設定文字顏色

設定未選擇的按鈕的按鈕文字的顏色。

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>參數

*clrText*<br/>
[在]RGB 顏色值。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a>CMFC按鈕::設定文字熱色

設置所選按鈕的按鈕文字的顏色。

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>參數

*clrTextHot*<br/>
[在]RGB 顏色值。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a>CMFC按鈕::設定工具提示

將工具提示與按鈕關聯。

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>參數

*lpszTool提示文字*<br/>
[在]指向工具提示的文本。 指定 NULL 以關閉工具提示。

### <a name="remarks"></a>備註

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFC按鈕::大小到內容

調整按鈕的大小以包含其按鈕文本和圖像。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
[在]真實計算,但不改變,按鈕的新大小;FALSE 以更改按鈕的大小。 預設值為 FALSE。

### <a name="return-value"></a>傳回值

包含`CSize`按鈕的新大小的物件。

### <a name="remarks"></a>備註

預設情況下,此方法計算一個新大小,該大小包括 10 像素的水平邊距和 5 像素的垂直邊距。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl 類別](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton 類別](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton 類別](../../mfc/reference/cmfcmenubutton-class.md)
