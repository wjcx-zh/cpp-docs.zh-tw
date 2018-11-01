---
title: CMFCRibbonStatusBarPane 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
ms.openlocfilehash: 183fd879b09595dda1dcd6caa8a8299debb20b30
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449331"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane 類別

`CMFCRibbonStatusBarPane`類別會實作可以加入功能區狀態列的功能區項目。

## <a name="syntax"></a>語法

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|建構並初始化 `CMFCRibbonStatusBarPane` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|傳回定義最長可以顯示在窗格中，而不會截斷的文字字串的字串。|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|傳回目前的文字對齊方式的設定。|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|決定動畫是否正在進行中。|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|決定是否要將窗格位於功能區狀態列擴充區域中。|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(覆寫[CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder)。)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(覆寫[CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)。)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|定義可顯示在窗格中，而不會截斷的最長的文字字串。|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|將影像清單可以用於動畫指派窗格中。|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|設定文字對齊方式。|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|開始指派給窗格的動畫。|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|指派給窗格動畫就會停止。 。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|指派給窗格動畫停止時由架構呼叫。|

## <a name="example"></a>範例

下列範例示範如何在 `CMFCRibbonStatusBarPane` 類別中使用各種方法。 此範例示範如何建構`CMFCRibbonStatusBarPane`物件，設定狀態列窗格的標籤文字對齊方式，定義可顯示在 [狀態] 列窗格，而不會截斷、 附加至狀態列窗格可用於影像清單的最長文字nimation，並開始動畫。

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>需求

**標頭：** afxribbonstatusbarpane.h

##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

建構在狀態列中的窗格物件。

```
CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    BOOL bIsStatic=FALSE,
    HICON hIcon=NULL,
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);
```

### <a name="parameters"></a>參數

*nCmdID*<br/>
[in]指定命令 ID 的窗格。

*lpszText*<br/>
[in]指定要在窗格中顯示的文字字串。

*bIsStatic*<br/>
[in]如果為 TRUE，無法反白顯示 [狀態] 窗格，或可以按一下它選取。

*hIcon*<br/>
[in]指定要在窗格中顯示圖示的控制代碼。

*lpszAlmostLargeText*<br/>
[in]指定可以窗格所顯示的最長的文字字串。

*hBmpAnimationList*<br/>
[in]指定用於動畫影像清單的控制代碼。

*cxAnimation*<br/>
[in]指定寬度，單位為像素的影像清單，其中用於動畫中的圖示。

*clrTrnsp*<br/>
[in]用於動畫的影像清單內指定影像的透明色彩。

*uiAnimationListResID*<br/>
[in]指定用於動畫影像清單的資源識別碼。

##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText

取得狀態列窗格可以顯示的最長的文字字串。

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>傳回值

狀態列窗格可以顯示的最長的文字字串。

##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign

取得目前的標籤的狀態列窗格的文字對齊方式的設定。

```
int GetTextAlign() const;
```

### <a name="return-value"></a>傳回值

目前的文字對齊方式可以是下列其中之一：

- TA_LEFT

- TA_CENTER

- TA_RIGHT。

##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation

決定動畫是否正在進行中。

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>傳回值

如果動畫正在進行則為 TRUEFALSE 否則。

##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended

決定是否要將窗格位於功能區狀態列擴充區域中。

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>傳回值

如果窗格上狀態列擴充區域，則為 TRUE。 FALSE 否則。

##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>參數

[in]*CDC&#42;*<br/>

### <a name="remarks"></a>備註

##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>參數

[in]*pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation

指派給窗格動畫結束時，架構會呼叫這個方法。

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>備註

`StopAnimation` 方法呼叫`OnFinishAnimation`方法，您可以使用動畫結束時清除資料。

##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText

定義可顯示在 [狀態] 列窗格，而不會截斷的最長文字。

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>參數

*lpszAlmostLargeText*<br/>
[in]指定可以顯示在 [狀態] 列窗格，而不會截斷的最長字串。

### <a name="remarks"></a>備註

程式庫計算文字的大小， *lpszAlmostLargeText*指定，並據以調整大小的窗格。 如果它仍不適合在窗格中，文字會被截斷。

##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList

附加至影像清單可以用於動畫狀態列窗格。

```
void SetAnimationList(
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```

### <a name="parameters"></a>參數

*hBmpAnimationList*<br/>
[in]指定影像清單的控制代碼。

*cxAnimation*<br/>
[in]指定寬度，單位為像素的影像清單中的框架。

*clrTransp*<br/>
[in]指定影像清單的透明色彩。

*uiAnimationListResID*<br/>
[in]指定影像清單的資源識別碼。

### <a name="return-value"></a>傳回值

如果影像清單已成功連結至狀態列窗格;，則為 TRUE。FALSE 否則。

##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign

設定標籤的狀態列窗格的文字對齊方式。

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>參數

*nAlign*<br/>
[in]指定文字的對齊方式。

### <a name="remarks"></a>備註

*nAlign*可以有下列值之一：

- TA_LEFT： 靠左的對齊

- TA_CENTER： 置中對齊

- TA_RIGHT： 靠右對齊

##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation

開始動畫，您將指派給 窗格。

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>參數

*nFrameDelay*<br/>
[in]指定動畫畫面播放速率，以毫秒為單位。

*nDuration*<br/>
[in]指定要播放的動畫，以毫秒為單位的時間。 使用-1 為無限迴圈。

### <a name="remarks"></a>備註

您必須指定影像清單的控制代碼，然後再呼叫`StartAnimation`使用`SetAnimationList`。

##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation

停止動畫，您指派給狀態列窗格。

```
void StopAnimation();
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar 類別](../../mfc/reference/cmfcribbonstatusbar-class.md)
