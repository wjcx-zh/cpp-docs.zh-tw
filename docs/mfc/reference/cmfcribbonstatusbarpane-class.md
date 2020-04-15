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
ms.openlocfilehash: 554b9fe364c6a213e038416a605c17cdd4f8e7d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368791"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane 類別

類別`CMFCRibbonStatusBarPane`實現功能區元素,您可以將其添加到功能區狀態列中。

## <a name="syntax"></a>語法

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 功能狀態列::CMFC 功能狀態列窗格](#cmfcribbonstatusbarpane)|建構並初始化 `CMFCRibbonStatusBarPane` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能狀態列::獲取幾乎大文字](#getalmostlargetext)|傳回定義在窗格中顯示的最長文字字串而不截斷的字串。|
|[CMFC 狀態列::取得文字對齊](#gettextalign)|返回文本對齊的當前設置。|
|[CMFC 功能狀態列::動畫](#isanimation)|確定動畫是否正在進行。|
|[CMFC 功能狀態列:擴展](#isextended)|確定窗格是否位於功能區狀態列的擴展區域。|
|[CMFC 功能狀態列::繪製邊框](#ondrawborder)|(覆寫[CMFC 功能按鈕:OnDraw 邊框](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFC 功能狀態列::在填充背景](#onfillbackground)|( 覆[寫 CMFC 功能按鈕:: 在填充背景](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground)。|
|[CMFC 功能狀態列::設置幾乎大文字](#setalmostlargetext)|定義可在窗格中顯示的最長文字字串,而不會截斷。|
|[CMFC 功能狀態列::設定動畫清單](#setanimationlist)|為窗格分配可用於動畫的圖像清單。|
|[CMFC 狀態列窗格::設定文字對齊](#settextalign)|設置文本對齊方式。|
|[CMFC 功能狀態列::啟動動畫](#startanimation)|啟動分配給窗格的動畫。|
|[CMFC 功能狀態列::停止動畫](#stopanimation)|停止分配給窗格的動畫。 .|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能狀態列::完成動畫](#onfinishanimation)|當分配給窗格的動畫停止時,由框架調用。|

## <a name="example"></a>範例

下列範例示範如何在 `CMFCRibbonStatusBarPane` 類別中使用各種方法。 該範例展示如何建構`CMFCRibbonStatusBarPane`物件、設定狀態列窗格標籤的文本對齊方式、定義可在狀態列窗格中顯示的最長文本而不截斷、將可用於動畫的圖像清單附加到狀態列窗格以及啟動動畫。

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>需求

**標題:** afxribbon 狀態列列.h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFC 功能狀態列::CMFC 功能狀態列窗格

在狀態列中構造窗格物件。

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
[在]指定窗格的命令代碼。

*lpszText*<br/>
[在]指定要顯示在窗格中的文字字串。

*bIs靜態*<br/>
[在]如果為 TRUE,則無法通過按一下狀態窗格突出顯示或選擇狀態窗格。

*hIcon*<br/>
[在]指定要顯示在窗格上的圖示的句柄。

*lpsz 幾乎大文字*<br/>
[在]指定窗格可以顯示的最長文字字串。

*hBmp動畫清單*<br/>
[在]指定用於動畫的圖像清單的句柄。

*cx 動畫*<br/>
[在]指定用於動畫的圖像清單中圖示的寬度(以像素為單位)。

*克拉特恩普*<br/>
[在]指定用於動畫的影像清單中圖像的透明顏色。

*ui 動畫清單重新ID*<br/>
[在]指定用於動畫的圖像清單的資源識別碼。

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFC 功能狀態列::獲取幾乎大文字

取得狀態列窗格可以顯示的最長文字字串。

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>傳回值

狀態列窗格可以顯示的最長文字字串。

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFC 狀態列::取得文字對齊

獲取狀態列窗格標籤的文本對齊的當前設置。

```
int GetTextAlign() const;
```

### <a name="return-value"></a>傳回值

目前文字對齊方式可以是以下方式之一:

- TA_LEFT

- TA_CENTER

- TA_RIGHT

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFC 功能狀態列::動畫

確定動畫是否正在進行。

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>傳回值

如果動畫正在進行,則為 TRUE;否則。

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFC 功能狀態列:擴展

確定窗格是否位於功能區狀態列的擴展區域。

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>傳回值

如果窗格位於狀態列擴展區域上,則為 TRUE。 否則為 FALSE。

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFC 功能狀態列::繪製邊框

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>參數

[在]*CDC&#42;*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFC 功能狀態列::在填充背景

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFC 功能狀態列::完成動畫

當分配給窗格的動畫結束時,框架將調用此方法。

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>備註

`StopAnimation`方法調用`OnFinishAnimation`方法,可用於在動畫結束時清理數據。

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFC 功能狀態列::設置幾乎大文字

定義可在狀態列窗格中顯示的最長文本,而不會截斷。

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>參數

*lpsz 幾乎大文字*<br/>
[在]指定可在狀態列窗格上顯示的最長字串,而不會截斷。

### <a name="remarks"></a>備註

庫計算*lpszAlmostLargeText*指定的文字大小,並相應地調整窗格的大小。 如果文本仍不適合窗格,則文本將被截斷。

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFC 功能狀態列::設定動畫清單

附加到狀態列窗格的圖像清單,可用於動畫。

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

*hBmp動畫清單*<br/>
[在]指定影像清單的句柄。

*cx 動畫*<br/>
[在]指定圖像清單中幀的寬度(以像素為單位)。

*clrTransp*<br/>
[在]指定影像清單的透明顏色。

*ui 動畫清單重新ID*<br/>
[在]指定映像清單的資源代碼。

### <a name="return-value"></a>傳回值

如果影像清單已成功附加到狀態列窗格,則為 TRUE;如果圖像清單已成功附加到狀態列窗格。否則。

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFC 狀態列窗格::設定文字對齊

設置狀態列窗格標籤的文本對齊方式。

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>參數

*N 對齊*<br/>
[在]指定文字對齊方式。

### <a name="remarks"></a>備註

*nAlign*可以具有以下值之一:

- TA_LEFT:左對齊

- TA_CENTER:中心對齊

- TA_RIGHT:正確對齊

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFC 功能狀態列::啟動動畫

啟動分配給窗格的動畫。

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>參數

*n 幀延遲*<br/>
[在]指定動畫幀速率(以毫秒為單位)。

*nDuration*<br/>
[在]指定以毫秒為單位播放動畫的時間。 將 -1 用於無限迴圈。

### <a name="remarks"></a>備註

在使用`StartAnimation``SetAnimationList`呼叫之前,必須指定影像清單的句柄。

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFC 功能狀態列::停止動畫

停止分配給狀態列窗格的動畫。

```
void StopAnimation();
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar 類別](../../mfc/reference/cmfcribbonstatusbar-class.md)
