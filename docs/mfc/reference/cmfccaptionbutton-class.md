---
title: CMFCCaptionButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719d6bafc50a036831f4aef1dd34c293b4129a83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381526"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton 類別

`CMFCCaptionButton`類別實作的停駐窗格或迷你框架視窗的標題列顯示的按鈕。 Framework 通常會自動建立標題按鈕。

## <a name="syntax"></a>語法

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|建構 CMFCCaptionButton 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|傳回按鈕表示的命令。|
|[CMFCCaptionButton::GetIconID](#geticonid)|傳回與按鈕關聯的映像識別碼。|
|[CMFCCaptionButton::GetRect](#getrect)|傳回按鈕所佔據的矩形。|
|[CMFCCaptionButton::GetSize](#getsize)|傳回按鈕的高度與寬度。|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|指出是否要將標題列的高度設定為小型大小。|
|[CMFCCaptionButton::Move](#move)|設定視窗的顯示狀態與按鈕繪製位置。|
|[CMFCCaptionButton::OnDraw](#ondraw)|繪製標題按鈕。|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|設定迷你標題列的大小。|

## <a name="remarks"></a>備註

您可以衍生的類別[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)，並使用受保護的方法，`AddButton`要加入的迷你框架視窗的標題按鈕。

CPaneFrameWnd.h 定義兩種類型的標題按鈕的命令識別碼：

- AFX_CAPTION_BTN_PIN，停駐窗格支援自動隱藏模式時，會顯示 pin 碼 按鈕。

- AFX_CAPTION_BTN_CLOSE，它會顯示**關閉**按鈕窗格可以關閉或隱藏時。

## <a name="example"></a>範例

下列範例示範如何建構`CMFCCaptionButton`物件，並設定迷你標題列的大小。

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>需求

**標頭：** afxcaptionbutton.h

##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton

建構 `CMFCCaptionButton` 物件。

```
CMFCCaptionButton();


CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>參數

*nHit*<br/>
[in]與按鈕關聯的命令。

*bLeftAlign*<br/>
[in]指定按鈕是否靠左對齊。

下表列出可能的值，如*nHit*參數。

|值|命令|
|-----------|-------------|
|AFX_HTCLOSE|[關閉] 按鈕。|
|HTMINBUTTON|最小化按鈕。|
|HTMAXBUTTON|最大化 按鈕。|
|AFX_HTLEFTBUTTON|向左箭號按鈕。|
|AFX_HTRIGHTBUTTON|向右箭號按鈕。|
|AFX_HTMENU|向下箭號 功能表按鈕。|
|HTNOWHERE|預設值;不代表任何命令。|

### <a name="remarks"></a>備註

根據預設，標題按鈕不會與命令相關聯。

在右或向左對齊標題按鈕。

##  <a name="gethit"></a>  CMFCCaptionButton::GetHit

傳回按鈕表示的命令。

```
UINT GetHit() const;
```

### <a name="return-value"></a>傳回值

命令按鈕表示。

下表列出可能的傳回值。

|值|命令|
|-----------|-------------|
|AFX_HTCLOSE|[關閉] 按鈕。|
|HTMINBUTTON|最小化按鈕。|
|HTMAXBUTTON|最大化 按鈕。|
|AFX_HTLEFTBUTTON|向左箭號按鈕。|
|AFX_HTRIGHTBUTTON|向右箭號按鈕。|
|AFX_HTMENU|向下箭號 功能表按鈕。|
|HTNOWHERE|預設值;不代表任何命令。|

##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID

傳回與按鈕關聯的映像識別碼。

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>參數

*bHorz*<br/>
[in]適用於左或向右箭號映像識別碼;FALSE 表示向上或向下箭號映像識別碼。

*bMaximized*<br/>
[in]適用於最大化映像識別碼;FALSE 表示最小化映像識別碼。

### <a name="return-value"></a>傳回值

映像識別碼。

### <a name="remarks"></a>備註

參數指定的最小化的映像識別碼，或最大化標題按鈕。

##  <a name="getrect"></a>  CMFCCaptionButton::GetRect

傳回按鈕所佔據的矩形。

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>傳回值

矩形，表示按鈕的位置。

### <a name="remarks"></a>備註

如果看不到按鈕，則傳回大小為 0。

##  <a name="getsize"></a>  CMFCCaptionButton::GetSize

傳回按鈕的高度與寬度。

```
static CSize GetSize();
```

### <a name="return-value"></a>傳回值

按鈕的外部的大小。

### <a name="remarks"></a>備註

傳回的大小包含按鈕的邊界和邊框。

##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton

指出是否要將標題列的高度設定為小型大小。

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>傳回值

如果標題設定為小型大小;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="move"></a>  CMFCCaptionButton::Move

設定視窗的顯示狀態與按鈕繪製位置。

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>參數

*ptTo*<br/>
[in]新的位置。

*bHide*<br/>
[in]是否要顯示的按鈕。

##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw

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
[in]按鈕的裝置內容指標。

*bActive*<br/>
[in]是否要繪製作用中的按鈕影像。

*bHorz*<br/>
[in]保留供衍生類別中使用。

*bMaximized*<br/>
[in]是否要繪製最大化的按鈕影像。

*bDisabled*<br/>
[in]是否要繪製已啟用] 按鈕影像。

### <a name="remarks"></a>備註

*BMaximized*參數會使用最大化 按鈕時，或最小化按鈕。

##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton

設定迷你標題列的大小。

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

*bSet*<br/>
[in]適用於小型的標題列的高度;預設標題列的高度，則為 FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd 類別](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)
