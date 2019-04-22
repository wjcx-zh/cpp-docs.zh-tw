---
title: CMFCRibbonProgressBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: 7c16217378cb8825ca4605687770de177e720c1d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58778165"
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar 類別

實作以視覺效果指示長時間作業進度的控制項。

## <a name="syntax"></a>語法

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|建構並初始化 `CMFCRibbonProgressBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|傳回目前的進度。|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|傳回目前範圍的最大值。|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|傳回目前範圍的最小值。|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[cmfcribbonbaseelement:: Getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|指定是否在無限模式工作的進度列。|
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[cmfcribbonbaseelement:: Ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw)。)|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|設定進度列在無限的模式下運作。|
|[CMFCRibbonProgressBar::SetPos](#setpos)|設定目前的進度。|
|[CMFCRibbonProgressBar::SetRange](#setrange)|設定最小和最大值。|

## <a name="remarks"></a>備註

A`CMFCRibbonProgressBar`可以在兩個模式下操作： 一般和無限。 在一般的模式中，進度列填滿從左到右，並停止時它達到最大值。 在無限的模式中，進度列重複從填入的最小值的最大值。 您可以使用無限的模式，表示作業正在進行中，但是完成時間不明。

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonProgressBar` 類別中使用各種方法。 設定進度列的最小和最大值，並設定進度列的目前位置，範例會示範如何設定要使用無限的模式 （其中一項作業的完成時間是未知） 中，進度列。 此程式碼片段是一部分[MS Office 2007 示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxRibbonProgressBar.h

##  <a name="cmfcribbonprogressbar"></a>  CMFCRibbonProgressBar::CMFCRibbonProgressBar

建構並初始化[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)物件。

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>參數

*nID*<br/>
[in]指定功能區的進度列的命令 ID。

*nWidth*<br/>
[in]指定寬度，單位為像素功能區的進度列。

*nHeight*<br/>
[in]指定高度，單位為像素功能區的進度列。

##  <a name="getpos"></a>  CMFCRibbonProgressBar::GetPos

傳回目前的進度列位置。

```
int GetPos () const;
```

### <a name="return-value"></a>傳回值

值，表示目前的進度列位置。

### <a name="remarks"></a>備註

正在設定的範圍必須是所指定的範圍內[CMFCRibbonProgressBar::SetRange](#setrange)方法。

##  <a name="getrangemax"></a>  CMFCRibbonProgressBar::GetRangeMax

傳回目前進度列的最大值。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>傳回值

目前範圍的最大值。

### <a name="remarks"></a>備註

##  <a name="getrangemin"></a>  CMFCRibbonProgressBar::GetRangeMin

傳回目前進度列的最小範圍值。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>傳回值

目前範圍的最小值。

##  <a name="getregularsize"></a>  CMFCRibbonProgressBar::GetRegularSize

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

[in] *pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="isinfinitemode"></a>  CMFCRibbonProgressBar::IsInfiniteMode

指定是否在無限模式工作的進度列。

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>傳回值

如果進度列為無限的模式，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

在無限的模式中，進度列填滿重複從最小值的最大值。 您可以使用無限的模式，表示作業正在進行中，但是完成時間不明。

##  <a name="ondraw"></a>  CMFCRibbonProgressBar::OnDraw

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

[in] *pDC*<br/>

### <a name="remarks"></a>備註

##  <a name="setinfinitemode"></a>  CMFCRibbonProgressBar::SetInfiniteMode

設定進度列在無限的模式下運作。

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

*bSet*<br/>
[in]若要指定進度列是無限的模式，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

通常，如果進度列是無限的模式，它在告訴使用者的作業正在進行，但完成時間不明。 因此，進度列填滿重複從最小值的最大值。

##  <a name="setpos"></a>  CMFCRibbonProgressBar::SetPos

設定進度列目前位置。

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nPos*<br/>
[in]指定設定的進度列的位置。

*bRedraw*<br/>
[in]指定是否應該重新繪製進度列。

### <a name="remarks"></a>備註

正在設定的範圍必須是所指定的範圍內[CMFCRibbonProgressBar::SetRange](#setrange)方法。

##  <a name="setrange"></a>  CMFCRibbonProgressBar::SetRange

設定進度列的最小和最大值。

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>參數

*nMin*<br/>
[in]指定範圍的最小值。

*nMax*<br/>
[in]指定範圍的最大值。

### <a name="remarks"></a>備註

使用此方法來定義進度列範圍設定最小和最大值。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
