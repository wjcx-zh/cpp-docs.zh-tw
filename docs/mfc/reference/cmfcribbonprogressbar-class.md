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
ms.openlocfilehash: b7cbddbd4fca8379562b762fadbb3d2bda44f166
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753539"
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
|[CMFC 剪彩進度列:CMFC 剪綵進度列](#cmfcribbonprogressbar)|建構並初始化 `CMFCRibbonProgressBar` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 功能放大縮小字型功能 放大縮小字型功能](#getpos)|返回當前進度。|
|[CMFC功能進度列:取得山脈最大值](#getrangemax)|返回當前範圍的最大值。|
|[CMFC功能進展列:獲取蘭格明](#getrangemin)|返回當前範圍的最小值。|
|[CMFC 功能進度列:取得一般大小](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[CMFC 功能基礎元素:取得一般大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFC功能收集進度列::無限模式](#isinfinitemode)|指定進度條是否以無限模式工作。|
|[CMFC剪綵進度列:在畫上](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[CMFC 功能基礎元素:onDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFC 功能進度列::設定無限模式](#setinfinitemode)|將進度條設置在無限模式下工作。|
|[CMFC 功能進度列::設定Pos](#setpos)|設置當前進度。|
|[CMFC 功能進度列::設定範圍](#setrange)|設置最小值和最大值。|

## <a name="remarks"></a>備註

A`CMFCRibbonProgressBar`可以在兩種模式下運行:常規模式和無限模式。 在常規模式下,進度條從左到右填充,並在達到最大值時停止。 在無限模式下,進度條從最小值重複填充到最大值。 您可以使用無限模式來指示操作正在進行,但完成時間未知。

## <a name="example"></a>範例

下例示範如何在 `CMFCRibbonProgressBar` 類別中使用各種方法。 該示例演示如何將進度條設置為以無限模式工作(操作的完成時間未知),設置進度條的最小值和最大值,並設置進度條的當前位置。 此代碼段是 MS [Office 2007 演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonProgressBar.h

## <a name="cmfcribbonprogressbarcmfcribbonprogressbar"></a><a name="cmfcribbonprogressbar"></a>CMFC 剪彩進度列:CMFC 剪綵進度列

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
[在]指定功能區進度列的命令 ID。

*n 寬度*<br/>
[在]指定功能區進度條的寬度(以像素為單位)。

*nHeight*<br/>
[在]指定功能區進度條的高度(以像素為單位)。

## <a name="cmfcribbonprogressbargetpos"></a><a name="getpos"></a>CMFC 功能放大縮小字型功能 放大縮小字型功能

返回進度條的當前位置。

```
int GetPos () const;
```

### <a name="return-value"></a>傳回值

表示進度條的當前位置的值。

### <a name="remarks"></a>備註

正在設置的範圍必須在[CMFCRibbonProgressBar 指定的範圍內::setRange](#setrange)方法。

## <a name="cmfcribbonprogressbargetrangemax"></a><a name="getrangemax"></a>CMFC功能進度列:取得山脈最大值

返回進度條的當前最大值。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>傳回值

當前範圍的最大值。

### <a name="remarks"></a>備註

## <a name="cmfcribbonprogressbargetrangemin"></a><a name="getrangemin"></a>CMFC功能進展列:獲取蘭格明

返回進度條的當前最小範圍值。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>傳回值

當前範圍的最小值。

## <a name="cmfcribbonprogressbargetregularsize"></a><a name="getregularsize"></a>CMFC 功能進度列:取得一般大小

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonprogressbarisinfinitemode"></a><a name="isinfinitemode"></a>CMFC功能收集進度列::無限模式

指定進度條是否以無限模式工作。

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>傳回值

如果進度條處於無限模式,則為 TRUE;如果進度條處於無限模式。否則,FALSE。

### <a name="remarks"></a>備註

在無限模式下,進度條從最小值重複填充到最大值。 您可以使用無限模式來指示操作正在進行,但完成時間未知。

## <a name="cmfcribbonprogressbarondraw"></a><a name="ondraw"></a>CMFC剪綵進度列:在畫上

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcribbonprogressbarsetinfinitemode"></a><a name="setinfinitemode"></a>CMFC 功能進度列::設定無限模式

將進度條設置在無限模式下工作。

```cpp
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>參數

*bSet*<br/>
[在]TRUE 指定進度條處於無限模式;否則,FALSE。

### <a name="remarks"></a>備註

通常,如果進度條處於無限模式,則告訴使用者操作正在進行,但完成時間未知。 因此,進度條從最小值重複填充到最大值。

## <a name="cmfcribbonprogressbarsetpos"></a><a name="setpos"></a>CMFC 功能進度列::設定Pos

設置進度條的當前位置。

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nPos*<br/>
[在]指定將進度條設置為的位置。

*bredraw*<br/>
[在]指定是否應重繪進度條。

### <a name="remarks"></a>備註

正在設置的範圍必須在[CMFCRibbonProgressBar 指定的範圍內::setRange](#setrange)方法。

## <a name="cmfcribbonprogressbarsetrange"></a><a name="setrange"></a>CMFC 功能進度列::設定範圍

設置進度條的最小值和最大值。

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>參數

*nMin*<br/>
[在]指定範圍的最小值。

*nMax*<br/>
[在]指定範圍的最大值。

### <a name="remarks"></a>備註

使用此方法通過設置最小值和最大值來定義進度條的範圍。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)
