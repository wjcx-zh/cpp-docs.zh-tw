---
title: CMFCCaptionButton 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: fb47e4373bf53e66dd4af17c89fe2f761858fbfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367740"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton 類別

類`CMFCCaptionButton`實現一個按鈕,該按鈕顯示在停靠窗格或微型框架視窗的標題列上。 Framework 通常會自動建立標題按鈕。

## <a name="syntax"></a>語法

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCCaption按鈕:CMFCCaption按鈕](#cmfccaptionbutton)|建構 CMFCCaptionButton 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCCaption按鈕:取得Hit](#gethit)|返回由按鈕表示的命令。|
|[CMFCCaption按鈕::GetIconID](#geticonid)|返回與按鈕關聯的圖像 ID。|
|[CMFCCaption按鈕::取得 Rect](#getrect)|返回按鈕佔用的矩形。|
|[CMFCCaption按鈕:取得大小](#getsize)|返回按鈕的寬度和高度。|
|[CMFC標題按鈕::IsMini框架按鈕](#isminiframebutton)|指示標題列高度是否設置為迷你大小。|
|[CMFCCaption按鈕:移動](#move)|設置按鈕繪製位置和窗口顯示狀態。|
|[CMFCCaption按鈕:在畫上](#ondraw)|繪製標題按鈕。|
|[CMFCCaption按鈕::設定迷你框架按鈕](#setminiframebutton)|設置標題列的迷你大小。|

## <a name="remarks"></a>備註

可以從[CPaneFrameWnd 類](../../mfc/reference/cpaneframewnd-class.md)派生類,並使用`AddButton`受保護的方法 ,向迷你框架視窗添加字幕按鈕。

CPaneFrameWnd.h 為兩種類型的字幕按鈕定義命令 ID:

- AFX_CAPTION_BTN_PIN,當停靠窗格支援自動隱藏模式時,將顯示一個引腳按鈕。

- AFX_CAPTION_BTN_CLOSE,當窗格可以關閉或隱藏時,將顯示「**關閉**」按鈕。

## <a name="example"></a>範例

下面的範例展示如何建構`CMFCCaptionButton`物件並設置標題列的迷你大小。

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxcaption按鈕.h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaption按鈕:CMFCCaption按鈕

建構 `CMFCCaptionButton` 物件。

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>參數

*nHit*<br/>
[在]與按鈕關聯的命令。

*b 左對齊*<br/>
[在]指定按鈕是否向左對齊。

下表列出了*nHit*參數的可能值。

|值|Command|
|-----------|-------------|
|AFX_HTCLOSE|關閉按鈕。|
|HTMINBUTTON|最小化按鈕。|
|HTMAX 按鈕|最大化按鈕。|
|AFX_HTLEFTBUTTON|左箭頭按鈕。|
|AFX_HTRIGHTBUTTON|右箭頭按鈕。|
|AFX_HTMENU|向下箭頭功能表按鈕。|
|HTNOWHERE|默認值;不表示任何命令。|

### <a name="remarks"></a>備註

預設情況下,標題按鈕不與命令關聯。

標題按鈕在右側或左側對齊。

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaption按鈕:取得Hit

返回由按鈕表示的命令。

```
UINT GetHit() const;
```

### <a name="return-value"></a>傳回值

按鈕表示的命令。

下表列出了可能的返回值。

|值|Command|
|-----------|-------------|
|AFX_HTCLOSE|關閉按鈕。|
|HTMINBUTTON|最小化按鈕。|
|HTMAX 按鈕|最大化按鈕。|
|AFX_HTLEFTBUTTON|左箭頭按鈕。|
|AFX_HTRIGHTBUTTON|右箭頭按鈕。|
|AFX_HTMENU|向下箭頭功能表按鈕。|
|HTNOWHERE|默認值;不表示任何命令。|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCCaption按鈕::GetIconID

返回與按鈕關聯的圖像 ID。

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>參數

*布霍茲*<br/>
[在]左或右箭頭圖像指示為 TRUE;對於左側或右側箭頭圖像指示,用於向上或向下箭頭圖像指示。

*b 最大化*<br/>
[在]為最大化圖像 ID 而實現 TRUE;用於最小化圖像 ID 的 FALSE。

### <a name="return-value"></a>傳回值

圖像識別碼。

### <a name="remarks"></a>備註

參數指定圖像指示,以盡量減少或最大化字幕按鈕。

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaption按鈕::取得 Rect

返回按鈕佔用的矩形。

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>傳回值

表示按鈕位置的矩形。

### <a name="remarks"></a>備註

如果看不到該按鈕,則返回的大小為 0。

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaption按鈕:取得大小

返回按鈕的寬度和高度。

```
static CSize GetSize();
```

### <a name="return-value"></a>傳回值

按鈕的外部尺寸。

### <a name="remarks"></a>備註

返回的大小包括按鈕邊距和邊框。

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFC標題按鈕::IsMini框架按鈕

指示標題列高度是否設置為迷你大小。

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>傳回值

如果標題設置為最小大小,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaption按鈕:移動

設置按鈕繪製位置和窗口顯示狀態。

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

*ptto*<br/>
[在]新位置。

*bHide*<br/>
[在]是否顯示該按鈕。

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaption按鈕:在畫上

繪製標題按鈕。

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向按鈕的設備上下文。

*b 活動*<br/>
[在]是否繪製活動按鈕圖像。

*布霍茲*<br/>
[在]保留用於派生類。

*b 最大化*<br/>
[在]是否繪製最大化按鈕圖像。

*b 殘疾*<br/>
[在]是否繪製啟用的按鈕圖像。

### <a name="remarks"></a>備註

當按鈕為最大化或最小化按鈕時,將使用*b最大化*參數。

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaption按鈕::設定迷你框架按鈕

設置標題列的迷你大小。

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

*bSet*<br/>
[在]TRUE,適用於迷你標題欄高度;默認標題列高度的 FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
