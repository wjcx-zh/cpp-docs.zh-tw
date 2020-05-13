---
title: CMFCCaptionBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: c42b1ccb51a3c290e0887717d900543b8d5b277a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752624"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar 類別

對`CMFCCaptionBar`像是一個控制項列,可以顯示三個元素:按鈕、文本標籤和位圖。 它一次只能每個類型各顯示一個項目。 您可以將每個項目對齊控制項的左緣或右緣，或對齊中央。 您也可以將平面或 3D 樣式套用至標題列的上框線和下框線。

## <a name="syntax"></a>語法

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCCaption列:建立](#create)|創建標題列控制項並將其附加到`CMFCCaptionBar`物件。|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|指示是否可以在標題列及其父框架之間動態插入另一個窗格。 (覆蓋[CBasePane::DoesAllowDynInsert 之前](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCCaption列:啟用按鈕](#enablebutton)|啟用或禁用標題列上的按鈕。|
|[CMFCCaption列:取得對齊](#getalignment)|返回指定元素的對齊方式。|
|[CMFCCaptionbar:取得邊界大小](#getbordersize)|返回標題列的邊框大小。|
|[CMFCCaptionbar:取得按鈕](#getbuttonrect)|檢索標題列上按鈕的邊界矩形。|
|[CMFCCaptionbar:取得保證金](#getmargin)|返回標題條元素邊緣與標題條控制元件邊緣之間的距離。|
|[CMFCCaptionbar::是消息列模式](#ismessagebarmode)|指定字幕列是否處於消息列模式。|
|[CMFCCaption列:刪除點陣圖](#removebitmap)|從標題列中刪除位圖圖像。|
|[CMFCCaption列:刪除按鈕](#removebutton)|從標題列中刪除按鈕。|
|[CMFCCaption列:刪除圖示](#removeicon)|從標題列中刪除圖示。|
|[CMFCCaption列:刪除文字](#removetext)|從標題列中刪除文本標籤。|
|[CMFCCaption 列:設定點陣圖](#setbitmap)|設置標題列的點陣圖圖像。|
|[CMFCCaption列:設定邊框大小](#setbordersize)|設置標題列的邊框大小。|
|[CMFCCaption列:設定按鈕](#setbutton)|設置標題列的按鈕。|
|[CMFCCaption 列:設定按鈕按下](#setbuttonpressed)|指定按鈕是否保持按下狀態。|
|[CMFCCaption列:設定按鈕工具提示](#setbuttontooltip)|設置按鈕的工具提示。|
|[CMFCCaption 列:設定平面邊框](#setflatborder)|設置標題列的邊框樣式。|
|[CMFCCaption列:SetIcon](#seticon)|設置標題列的圖示。|
|[CMFC 標題列::設定影像工具提示](#setimagetooltip)|設置標題列的圖像工具提示。|
|[CMFCCaption列:設定邊緣](#setmargin)|設置標題條元素邊緣與標題條控制元件邊緣之間的距離。|
|[CMFCCaption列:設定文字](#settext)|設置標題列的文本標籤。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCCaptionbar:在繪製背景](#ondrawbackground)|由框架呼叫以填充標題列的背景。|
|[CMFCCaptionbar:OnDraw邊框](#ondrawborder)|由框架調用以繪製標題列的邊框。|
|[CMFCCaptionbar:在繪製按鈕](#ondrawbutton)|由框架調用以繪製標題欄按鈕。|
|[CMFCCaptionbar:在影像上](#ondrawimage)|由框架調用以繪製標題欄圖像。|
|[CMFCCaptionbar:onDrawtext](#ondrawtext)|由框架調用以繪製標題欄文本。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCCaptionbar:m_clrBarBackground](#m_clrbarbackground)|標題列的背景顏色。|
|[CMFCCaptionbar:m_clrBarBorder](#m_clrbarborder)|標題列邊框的顏色。|
|[CMFCCaptionbar:m_clrBarText](#m_clrbartext)|標題列文字的顏色。|

## <a name="remarks"></a>備註

要建立標題列,請按照以下步驟操作:

1. 建構 `CMFCCaptionBar` 物件。 通常,您將字幕列添加到框架視窗類。

1. 調用[CMFCCaptionBar::創建](#create)方法來創建字幕欄控件並將其`CMFCCaptionBar`附加到 物件。

1. 呼叫[CMFCCaption 欄:設定按鈕](#setbutton)[,CMFCCaption 欄:設定文本](#settext)[,CMFCCaption 欄::SetIcon,](#seticon)和[CMFCCaption 欄::SetBitmap](#setbitmap)設置標題列元素。

設置按鈕元素時,必須為按鈕分配命令 ID。 當用戶按下這個按鈕時,標題列會將具有此 ID 的WM_COMMAND消息路由到父框架視窗。

標題列也可以在消息列模式下工作,該模式類比 Microsoft Office 2007 應用程式中出現的消息列。 在消息列模式下,標題列顯示位圖、消息和按鈕(通常打開對話框)。您可以為點陣圖分配工具提示。

要啟用消息列模式,請致電[CMFCCaptionBar::創建](#create)並將第四個參數(bIsMessageBarMode)設置為 TRUE。

## <a name="example"></a>範例

下例示範如何在 `CMFCCaptionBar` 類別中使用各種方法。 這個範例展示如何建立標題列控制、設定字幕列的 3D 邊框、設定字幕列元素邊緣和標題列控制元件邊緣之間的距離(以像素為單位)、設定標題列的按鈕、設定按鈕的工具提示、設定字幕列的文字標籤、設定標題列的位圖圖像並在標題列中設置圖像的工具提示。 此代碼段是 MS [Office 2007 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>需求

**標題:** afxcaptionbar.h

## <a name="cmfccaptionbarcreate"></a><a name="create"></a>CMFCCaption列:建立

創建標題列控制項並將其附加到`CMFCCaptionBar`物件。

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
標題列樣式的邏輯 OR 組合。

*pparentwnd*<br/>
標題列控制項的父視窗。

*Uid*<br/>
標題列控制項的識別碼。

*nHeight*<br/>
標題欄控件的高度(以像素為單位)。 如果為 -1,則根據圖示的高度、文本和標題列控件顯示的按鈕計算高度。

*bIsMessageBar 模式*<br/>
如果標題欄處於消息欄模式,則為 TRUE;如果標題欄處於消息欄模式。"否則。

### <a name="return-value"></a>傳回值

如果字幕列控制項已成功建立,則為 TRUE;如果字幕列控制項已成功建立,則為 TRUE。否則。

### <a name="remarks"></a>備註

分兩步`CMFCCaptionBar`構造物件。 首先調用構造函數,然後調用`Create`方法,該方法創建 Windows 控件並將其`CMFCCaptionBar`附加到 物件。

## <a name="cmfccaptionbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCCaption列::DoesAllowDynInsert之前

指示是否可以在標題列及其父框架之間動態插入另一個窗格。

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

返回 FALSE,除非重寫。

### <a name="remarks"></a>備註

## <a name="cmfccaptionbarenablebutton"></a><a name="enablebutton"></a>CMFCCaption列:啟用按鈕

啟用或禁用標題列上的按鈕。

```cpp
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*b 啟用*<br/>
[在]TRUE 啟用按鈕,FALSE 禁用該按鈕。

## <a name="cmfccaptionbargetalignment"></a><a name="getalignment"></a>CMFCCaption列:取得對齊

返回指定元素的對齊方式。

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>參數

*埃萊姆*<br/>
[在]要為其檢索對齊的標題欄元素。

### <a name="return-value"></a>傳回值

元素(如按鈕、位圖、文本或圖示)的對齊方式。

### <a name="remarks"></a>備註

元素的對齊可以是以下值之一:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbargetbordersize"></a><a name="getbordersize"></a>CMFCCaptionbar:取得邊界大小

返回標題列的邊框大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>傳回值

邊框的大小(以像素為單位)。

## <a name="cmfccaptionbargetbuttonrect"></a><a name="getbuttonrect"></a>CMFCCaptionbar:取得按鈕

檢索標題列上按鈕的邊界矩形。

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>傳回值

包含`CRect`標題列上按鈕邊界矩形的座標的物件。

## <a name="cmfccaptionbargetmargin"></a><a name="getmargin"></a>CMFCCaptionbar:取得保證金

返回標題條元素邊緣與標題條控制元件邊緣之間的距離。

```
int GetMargin() const;
```

### <a name="return-value"></a>傳回值

標題條元素邊緣與標題條控制件邊緣之間的距離(以像素為單位)。

## <a name="cmfccaptionbarismessagebarmode"></a><a name="ismessagebarmode"></a>CMFCCaptionbar::是消息列模式

指定字幕列是否處於消息列模式。

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>傳回值

如果標題欄處於消息欄模式,則為 TRUE;如果標題欄處於消息欄模式。"否則。

### <a name="remarks"></a>備註

在消息列模式下,標題列顯示帶有工具提示、消息文本和按鈕的圖像。

## <a name="cmfccaptionbarm_clrbarbackground"></a><a name="m_clrbarbackground"></a>CMFCCaptionbar:m_clrBarBackground

標題列的背景顏色。

```
COLORREF m_clrBarBackground
```

## <a name="cmfccaptionbarm_clrbarborder"></a><a name="m_clrbarborder"></a>CMFCCaptionbar:m_clrBarBorder

標題列邊框的顏色。

```
COLORREF m_clrBarBorder
```

## <a name="cmfccaptionbarm_clrbartext"></a><a name="m_clrbartext"></a>CMFCCaptionbar:m_clrBarText

標題列文字的顏色。

```
COLORREF m_clrBarText
```

## <a name="cmfccaptionbarondrawbackground"></a><a name="ondrawbackground"></a>CMFCCaptionbar:在繪製背景

由框架呼叫以填充標題列的背景。

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向字幕欄的設備上下文的指標。

*矩形*<br/>
[在]要填充的邊界矩形。

### <a name="remarks"></a>備註

當`OnDrawBackground`標題列的背景即將填充時,將調用該方法。 預設實現使用[CMFCCaptionBar:::m_clrBarBackground](#m_clrbarbackground)顏色填充背景。

在`CMFCCaptionBar`派生類中重寫此方法以自定義標題欄的外觀。

## <a name="cmfccaptionbarondrawborder"></a><a name="ondrawborder"></a>CMFCCaptionbar:OnDraw邊框

由框架調用以繪製標題列的邊框。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]用於顯示邊框的設備上下文。

*矩形*<br/>
[在]邊界矩形。

### <a name="remarks"></a>備註

默認情況下,邊框具有平面樣式。

在`CMFCCaptionBar`派生類中重寫此方法以自定義字幕欄邊框的外觀。

## <a name="cmfccaptionbarondrawbutton"></a><a name="ondrawbutton"></a>CMFCCaptionbar:在繪製按鈕

由框架調用以繪製標題欄按鈕。

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於顯示按鈕的設備上下文的指標。

*矩形*<br/>
[在]按鈕的邊界矩形。

*斯特按鈕*<br/>
[在]按鈕的文字標籤。

*b 啟用*<br/>
[在]如果啟用了按鈕,則為 TRUE;否則。

### <a name="remarks"></a>備註

在`CMFCCaptionBar`派生類中重寫此方法以自定義字幕欄按鈕的外觀。

## <a name="cmfccaptionbarondrawimage"></a><a name="ondrawimage"></a>CMFCCaptionbar:在影像上

由框架調用以繪製標題欄圖像。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於顯示圖像的設備上下文的指標。

*矩形*<br/>
[在]指定圖像的邊界矩形。

### <a name="remarks"></a>備註

在`CMFCCaptionBar`派生類中重寫此方法以自定義圖像外觀。

## <a name="cmfccaptionbarondrawtext"></a><a name="ondrawtext"></a>CMFCCaptionbar:onDrawtext

由框架調用以繪製標題欄文本。

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於顯示按鈕的設備上下文的指標。

*矩形*<br/>
[在]文本的邊界矩形。

*斯特文字*<br/>
[在]要顯示的文字字串。

### <a name="remarks"></a>備註

預設實現使用`CDC::DrawText`和[CMFCCaptionBar::m_clrBarText](#m_clrbartext)顏色來顯示文本。

在`CMFCCaptionBar`派生類中重寫此方法以自定義字幕欄文本的外觀。

## <a name="cmfccaptionbarremovebitmap"></a><a name="removebitmap"></a>CMFCCaption列:刪除點陣圖

從標題列中刪除位圖圖像。

```cpp
void RemoveBitmap();
```

## <a name="cmfccaptionbarremovebutton"></a><a name="removebutton"></a>CMFCCaption列:刪除按鈕

從標題列中刪除按鈕。

```cpp
void RemoveButton();
```

### <a name="remarks"></a>備註

字幕條元素的佈局會自動調整。

## <a name="cmfccaptionbarremoveicon"></a><a name="removeicon"></a>CMFCCaption列:刪除圖示

從標題列中刪除圖示。

```cpp
void RemoveIcon();
```

## <a name="cmfccaptionbarremovetext"></a><a name="removetext"></a>CMFCCaption列:刪除文字

從標題列中刪除文本標籤。

```cpp
void RemoveText();
```

## <a name="cmfccaptionbarsetbitmap"></a><a name="setbitmap"></a>CMFCCaption 列:設定點陣圖

設置標題列的點陣圖圖像。

```cpp
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
[在]要設置的點陣圖的句柄。

*clr透明*<br/>
[在]指定點陣圖的透明顏色的 RGB 值。

*b 伸*<br/>
[在]如果為 TRUE,則如果位圖不適合影像邊界矩形,則位圖將拉伸。 否則,位圖不會拉伸。

*bmp 對齊*<br/>
[在]位圖的對齊方式。

### <a name="remarks"></a>備註

使用此方法在標題列上設置點陣圖。

以前的點陣圖將自動銷毀。 如果標題列顯示圖示,因為您調用了[CMFCCaptionBar::setIcon](#seticon)方法,則除非通過調用[CMFCCaptionBar::::刪除圖示](#removeicon)來刪除該圖示,否則將不會顯示位圖。

位圖按*bmpAlignment 參數*指定對齊。  這個參數可以是下列其中一個 `BarElementAlignment` 值：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetbordersize"></a><a name="setbordersize"></a>CMFCCaption列:設定邊框大小

設置標題列的邊框大小。

```cpp
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
[在]標題列邊框的新大小(以像素為單位)。

## <a name="cmfccaptionbarsetbutton"></a><a name="setbutton"></a>CMFCCaption列:設定按鈕

設置標題列的按鈕。

```cpp
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
按鈕的命令標籤。

*烏伊CmdUI*<br/>
按鈕的命令識別碼。

*btnalignmnet*<br/>
按鈕的對齊方式。

*b哈斯下拉箭頭*<br/>
如果按鈕顯示下拉箭頭,則為 TRUE,否則為 FALSE。

## <a name="cmfccaptionbarsetbuttonpressed"></a><a name="setbuttonpressed"></a>CMFCCaption 列:設定按鈕按下

指定按鈕是否保持按下狀態。

```cpp
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>參數

*bPresed*<br/>
如果按鈕保持其按下狀態,則為 TRUE,否則為 FALSE。

## <a name="cmfccaptionbarsetbuttontooltip"></a><a name="setbuttontooltip"></a>CMFCCaption列:設定按鈕工具提示

設置按鈕的工具提示。

```cpp
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>參數

*lpszToolTip*<br/>
[在]工具提示標題。

*lpsz描述*<br/>
[在]工具提示說明。

## <a name="cmfccaptionbarsetflatborder"></a><a name="setflatborder"></a>CMFCCaption 列:設定平面邊框

設置標題列的邊框樣式。

```cpp
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>參數

*bFlat*<br/>
[在]如果標題列的邊框是平面的,則為 TRUE。 如果邊框為 3D,則 FALSE。

## <a name="cmfccaptionbarseticon"></a><a name="seticon"></a>CMFCCaption列:SetIcon

設置標題列的圖示。

```cpp
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>參數

*hIcon*<br/>
[在]要設置的圖示的句柄。

*圖示對齊*<br/>
[在]圖示的對齊方式。

### <a name="remarks"></a>備註

標題列可以顯示圖示或點陣圖。 請參閱[CMFCCaption 欄:SetBitmap](#setbitmap)以瞭解如何顯示點陣圖。 如果同時設置圖示和位圖,則始終顯示該圖示。 呼叫[CMFCCaption 列:刪除圖示](#removeicon)以從字幕列中刪除圖示。

圖示根據*圖示對齊參數對齊*。 它可以是以下`BarElementAlignment`值之一:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="cmfccaptionbarsetimagetooltip"></a><a name="setimagetooltip"></a>CMFC 標題列::設定影像工具提示

在標題列中設置圖像的工具提示。

```cpp
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>參數

*lpszToolTip*<br/>
[在]工具提示的文字。

*lpsz描述*<br/>
[在]工具提示說明。

## <a name="cmfccaptionbarsetmargin"></a><a name="setmargin"></a>CMFCCaption列:設定邊緣

設置標題條元素邊緣與標題條控制元件邊緣之間的距離。

```cpp
void SetMargin(int nMargin);
```

### <a name="parameters"></a>參數

*nMargin*<br/>
[在]標題條元素邊緣與標題條控制件邊緣之間的距離(以像素為單位)。

## <a name="cmfccaptionbarsettext"></a><a name="settext"></a>CMFCCaption列:設定文字

設置標題列的文本標籤。

```cpp
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>參數

*斯特文字*<br/>
[在]要設置的文字字串。

*文字對齊*<br/>
[在]文本對齊。

### <a name="remarks"></a>備註

文字標籤按*文字對齊*參數指定對齊。 它可以是以下`BarElementAlignment`值之一:

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
