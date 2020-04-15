---
title: CMFCAutoHideButton 類別
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
ms.openlocfilehash: 84f17896cc3c4f5cd6099a9ccf7e4e000f43b1f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369915"
---
# <a name="cmfcautohidebutton-class"></a>CMFCAutoHideButton 類別

可顯示或隱藏 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) (設定為隱藏) 的按鈕。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCAutoHideButton : public CObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCAutoHideButton::BringToTop](#bringtotop)||
|[CMFCAutoHideButton::Create](#create)|建立並初始化自動隱藏按鈕。|
|[CMFCAutoHideButton::GetAlignment](#getalignment)|擷取自動隱藏按鈕的對齊方式。|
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|返回與自動隱藏按鈕關聯的[CDockablePane](../../mfc/reference/cdockablepane-class.md)物件。|
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||
|[CMFCAutoHideButton::GetRect](#getrect)||
|[CMFCAutoHideButton::GetSize](#getsize)|決定自動隱藏按鈕的大小。|
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|傳回自動隱藏按鈕文字標籤的大小。|
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|反白顯示自動隱藏按鈕。|
|[CMFCAutoHideButton::IsActive](#isactive)|指出自動隱藏按鈕是否為作用中。|
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|傳回自動隱藏按鈕反白顯示的狀態。|
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|判斷自動隱藏按鈕是水平或垂直。|
|[CMFCAutoHideButton::IsTop](#istop)||
|[CMFCAutoHideButton::IsVisible](#isvisible)|指出是否顯示按鈕。|
|[CMFCAutoHideButton::Move](#move)||
|[CMFCAutoHideButton::OnDraw](#ondraw)|當它繪製自動隱藏按鈕時，架構會呼叫這個方法。|
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|當它繪製自動隱藏按鈕的邊框時，架構會呼叫這個方法。|
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|當它填入自動隱藏按鈕的背景時，架構會呼叫這個方法。|
|[CMFCAutoHideButton::ReplacePane](#replacepane)||
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|顯示或隱藏關聯的[可載窗格類別](../../mfc/reference/cdockablepane-class.md)。|
|[CMFCAutoHideButton::ShowButton](#showbutton)|顯示或隱藏自動隱藏按鈕。|
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||

## <a name="remarks"></a>備註

在建立時,`CMFCAutoHideButton`物件附加到[可載板類別](../../mfc/reference/cdockablepane-class.md)。 `CDockablePane` 物件會隨著使用者與 `CMFCAutoHideButton` 物件的互動隱藏或顯示。

根據預設，當使用者開啟自動隱藏時，架構會自動建立 `CMFCAutoHideButton`。 架構可以建立自訂 UI 類別而不是 `CMFCAutoHideButton` 類別的項目。 若要指定架構應該使用的自訂 UI 類別，請將靜態成員變數 `CMFCAutoHideBar::m_pAutoHideButtonRTS` 設定為等於自訂 UI 類別。 根據預設，此變數會設為 `CMFCAutoHideButton`。

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCAutoHideButton` 物件，以及使用 `CMFCAutoHideButton` 類別中的各種方法。 此範例示範如何初始化 `CMFCAutoHideButton` 物件 (使用其 `Create` 方法)，顯示相關聯的 `CDockablePane` 類別，並顯示自動隱藏按鈕。

[!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAutoHideButton`

## <a name="requirements"></a>需求

**標頭：** afxautohidebutton.h

## <a name="cmfcautohidebuttonbringtotop"></a><a name="bringtotop"></a>CMFC自動隱藏按鈕::帶上頂部

```
void BringToTop();
```

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttoncreate"></a><a name="create"></a>CMFC 自動隱藏按鈕::建立

建立並初始化自動隱藏按鈕。

```
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>參數

*p 父列*<br/>
[在]指向父工具列的指標。

*pAutoHidewnd*<br/>
[在]指向[可多克窗格物件的指標](../../mfc/reference/cdockablepane-class.md)。 此自動隱藏按鍵隱藏並顯示`CDockablePane`。

*dwalignment*<br/>
[在]指定按鈕與主框架視窗對齊的值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

建立`CMFCAutoHideButton`物件時,必須將自動隱藏按鈕與特定`CDockablePane`的 。 使用者可以使用自動隱藏按鍵隱藏與顯示關聯的`CDockablePane`。

*dwAlignment*參數指示自動隱藏按鈕駐留在應用程式中的位置。 這個參數可以是下列任何一個值：

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetalignment"></a><a name="getalignment"></a>CMFC自動隱藏按鈕::獲取對齊

擷取自動隱藏按鈕的對齊方式。

```
DWORD GetAlignment() const;
```

### <a name="return-value"></a>傳回值

包含自動隱藏按鈕的當前對齊方式的 DWORD 值。

### <a name="remarks"></a>備註

自動隱藏按鈕的對齊方式指示按鈕駐留在應用程式上的位置。 它可以是以下任一值:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CRBS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebuttongetautohidewindow"></a><a name="getautohidewindow"></a>CMFC 自動隱藏按鈕::抓取自動隱藏視窗

返回與自動隱藏按鈕關聯的[CDockablePane](../../mfc/reference/cdockablepane-class.md)物件。

```
CDockablePane* GetAutoHideWindow() const;
```

### <a name="return-value"></a>傳回值

指向關聯`CDockablePane`物件的指標。

### <a name="remarks"></a>備註

要將自動隱藏按鈕與 相關`CDockablePane`聯`CDockablePane`,請將 作為參數傳遞給[CMFCAutoHideButton::create](#create)方法。

## <a name="cmfcautohidebuttongetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFC自動隱藏按鈕::取得父項目工具列

```
CMFCAutoHideBar* GetParentToolBar();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttongetrect"></a><a name="getrect"></a>CMFC自動隱藏按鈕::取得 Rect

```
CRect GetRect() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttongetsize"></a><a name="getsize"></a>CMFC 自動隱藏按鈕:取得大小

決定自動隱藏按鈕的大小。

```
CSize GetSize() const;
```

### <a name="return-value"></a>傳回值

包含`CSize`按鈕大小的物件。

### <a name="remarks"></a>備註

計算的大小包括自動隱藏按鈕的邊框大小。

## <a name="cmfcautohidebuttongettextsize"></a><a name="gettextsize"></a>CMFC 自動隱藏按鈕::取得文字大小

傳回自動隱藏按鈕文字標籤的大小。

```
virtual CSize GetTextSize() const;
```

### <a name="return-value"></a>傳回值

包含自動隱藏按鈕的文字大小的[CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

## <a name="cmfcautohidebuttonisactive"></a><a name="isactive"></a>CMFC 自動隱藏按鈕::活動

指出自動隱藏按鈕是否為作用中。

```
BOOL IsActive() const;
```

### <a name="return-value"></a>傳回值

如果自動隱藏按鈕處於活動狀態,則為 TRUE;否則。

### <a name="remarks"></a>備註

顯示關聯的[CDockablePane 類](../../mfc/reference/cdockablepane-class.md)視窗時,自動隱藏按鈕處於活動狀態。

## <a name="cmfcautohidebuttonishorizontal"></a><a name="ishorizontal"></a>CMFC自動隱藏按鈕::是水準的

判斷自動隱藏按鈕是水平或垂直。

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>傳回值

如果按鈕是水準的,則非零;0 否則。

### <a name="remarks"></a>備註

框架在創建[CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)物件時設置其方向。  您可以使用[CMFCAutoHideButton::create](#create)方法中的*dwAlignment*參數來控制方向。

## <a name="cmfcautohidebuttonistop"></a><a name="istop"></a>CMFC自動隱藏按鈕::是頂部

```
BOOL IsTop() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttonisvisible"></a><a name="isvisible"></a>CMFC 自動隱藏按鈕:可見

指示自動隱藏按鈕是否可見。

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>傳回值

如果按鈕可見,則為 TRUE;否則。

## <a name="cmfcautohidebuttonondraw"></a><a name="ondraw"></a>CMFC自動隱藏按鈕::開機

當它繪製自動隱藏按鈕時，架構會呼叫這個方法。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

### <a name="remarks"></a>備註

如果要自定義應用程式中自動隱藏按鈕的外觀,請創建派生自`CMFCAutoHideButton`的新類。 在派生類中,重寫此方法。

## <a name="cmfcautohidebuttonondrawborder"></a><a name="ondrawborder"></a>CMFC自動隱藏按鈕::在繪製邊框

當它繪製自動隱藏按鈕的邊框時，架構會呼叫這個方法。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*rectBunds*<br/>
[在]自動隱藏按鈕的邊界矩形。

*整邊界大小*<br/>
[在]自動隱藏按鈕每側的邊框厚度。

### <a name="remarks"></a>備註

如果要自訂應用程式中每個自動隱藏按鈕的邊框,請建立派生自 的新`CMFCAutoHideButton`類 。 在派生類中,重寫此方法。

## <a name="cmfcautohidebuttononfillbackground"></a><a name="onfillbackground"></a>CMFC自動隱藏按鈕::在填充背景

當它填入自動隱藏按鈕的背景時，架構會呼叫這個方法。

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]自動隱藏按鈕的邊界矩形。

### <a name="remarks"></a>備註

如果您要自訂應用程式中自動隱藏按鈕的背景,請建立派生自的新`CMFCAutoHideButton`類 。 在派生類中,重寫此方法。

## <a name="cmfcautohidebuttonshowattachedwindow"></a><a name="showattachedwindow"></a>CMFC 自動隱藏按鈕:顯示額外視窗

顯示或隱藏關聯的[可載窗格類別](../../mfc/reference/cdockablepane-class.md)。

```
void ShowAttachedWindow(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
[在]指定此方法是否顯示附加`CDockablePane`的 布林。

## <a name="cmfcautohidebuttonshowbutton"></a><a name="showbutton"></a>CMFC 自動隱藏按鈕::顯示按鈕

顯示或隱藏自動隱藏按鈕。

```
virtual void ShowButton(BOOL bShow);
```

### <a name="parameters"></a>參數

*b 顯示*<br/>
[在]指定是否顯示自動隱藏按鈕的布林。

## <a name="cmfcautohidebuttonmove"></a><a name="move"></a>CMFC 自動隱藏按鈕:移動

```
void Move(int nOffset);
```

### <a name="parameters"></a>參數

[在]*n位移*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttonreplacepane"></a><a name="replacepane"></a>CMFC 自動隱藏按鈕::取代窗格

```
void ReplacePane(CDockablePane* pNewBar);
```

### <a name="parameters"></a>參數

[在]*pNewBar*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttonunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFC 自動隱藏按鈕:取消設定自動隱藏模式

停用自動隱藏模式。

```
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```

### <a name="parameters"></a>參數

*普第一巴林集團*<br/>
[在]指向組中的第一個條形的指標。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttonhighlightbutton"></a><a name="highlightbutton"></a>CMFC自動隱藏按鈕::高光按鈕

突出顯示自動隱藏按鈕。

```
virtual void HighlightButton(BOOL bHighlight);
```

### <a name="parameters"></a>參數

*b 高光*<br/>
指定新的自動隱藏按鈕狀態。 TRUE 表示按鈕高亮顯示,FALSE 表示按鈕未突出顯示。

### <a name="remarks"></a>備註

## <a name="cmfcautohidebuttonishighlighted"></a><a name="ishighlighted"></a>CMFC 自動隱藏按鈕::已突出顯示

返回自動隱藏按鈕的高光狀態。

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>傳回值

如果自動隱藏按鈕突出顯示,則返回 TRUE;如果自動隱藏按鈕突出顯示,則返回 TRUE。否則 FALSE。

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAutoHideBar 類別](../../mfc/reference/cmfcautohidebar-class.md)<br/>
[CAutoHideDockSite 類別](../../mfc/reference/cautohidedocksite-class.md)
