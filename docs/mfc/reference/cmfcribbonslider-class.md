---
title: CMFC 剪桿級
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: 304581371c68817c6031153c3cec227137771c5d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754070"
---
# <a name="cmfcribbonslider-class"></a>CMFC 剪桿級

類`CMFCRibbonSlider`實現滑動器控制項,您可以將該控制項添加到功能區列或功能區狀態列中。 功能區滑桿控制項類似出現在 Office 2007 應用程式中的縮放滑桿。

## <a name="syntax"></a>語法

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC剪彩滑塊:CMFC剪綵滑塊](#cmfcribbonslider)|構造和初始化功能區滑塊控制元件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC剪桿:GetPos](#getpos)|返回滑塊控制項的目前位置。|
|[CMFC剪綵滑塊:獲取山脈最大值](#getrangemax)|返回滑塊的最大值。|
|[CMFC剪綵者:獲取蘭格明](#getrangemin)|返回滑塊的最小值。|
|[CMFC 功能滑動器:取得一般大小](#getregularsize)|傳回功能區項目的一般大小。 (覆寫[CMFC 功能基礎元素:取得一般大小](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFC 功能滑塊::取得放大增量](#getzoomincrement)|返回滑塊控制件的縮放增量大小。|
|[CMFC 功能滑動器::有縮放按鈕](#haszoombuttons)|指定滑塊是否具有縮放按鈕。|
|[CMFC剪綵器:在畫上](#ondraw)|由架構呼叫以繪製功能區項目。 (覆寫[CMFC 功能基礎元素:onDraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw).)|
|[CMFC 剪桿::設置Pos](#setpos)|設置滑塊控制的當前位置。|
|[CMFC 剪桿滑塊::設定範圍](#setrange)|通過設置最小值和最大值來指定滑塊控制項的範圍。|
|[CMFC 功能滑動器:設定縮放按鈕](#setzoombuttons)|顯示或隱藏縮放按鈕。|
|[CMFC 功能滑塊::設定放大增量](#setzoomincrement)|設置滑塊控制的縮放增量大小。|

## <a name="remarks"></a>備註

可以使用方法`SetRange`配置滑塊的縮放增量範圍。 您可以使用`SetPos`方法設定滑塊的當前位置。

您可以使用`SetZoomButtons`方法在滑塊控制元件的左側和右側顯示圓形縮放按鈕。 默認情況下,滑塊是水準的,左側縮放按鈕顯示減號,右側縮放按鈕顯示加號。

該方法`SetZoomIncrement`定義在使用者按下縮放按鈕時要添加到或從當前位置減去的增量。

## <a name="example"></a>範例

下面的範例展示如何在`CMFCRibbonSlider`類中使用各種方法來設置滑塊的屬性。 該示例演示如何建構`CMFCRibbonSlider`對象、顯示縮放按鈕、設置滑塊控制項的當前位置以及設置滑塊控制項的值範圍。

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>需求

**標題:** afxribbon 滑塊.h

## <a name="cmfcribbonslidercmfcribbonslider"></a><a name="cmfcribbonslider"></a>CMFC剪彩滑塊:CMFC剪綵滑塊

構造功能區滑塊。

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]滑塊識別碼。

[在]。 *n 寬度*滑塊寬度(以像素為單位)。

### <a name="remarks"></a>備註

建構在添加滑塊的面板類別中為*nWidth*像素寬的功能區滑塊。 默認情況下,滑塊是水準的。

## <a name="cmfcribbonslidergetpos"></a><a name="getpos"></a>CMFC剪桿:GetPos

返回滑塊控制項的目前位置。

```
int GetPos() const;
```

### <a name="return-value"></a>傳回值

滑塊控制項的目前位置,該位置相對於滑塊的開頭。

## <a name="cmfcribbonslidergetrangemax"></a><a name="getrangemax"></a>CMFC剪綵滑塊:獲取山脈最大值

獲取滑塊可以在滑塊控制件上移動的最大增量。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>傳回值

滑塊可以在滑塊控制件上移動的滑塊的最大增量。

## <a name="cmfcribbonslidergetrangemin"></a><a name="getrangemin"></a>CMFC剪綵者:獲取蘭格明

返回滑塊在滑塊控制件上可以移動的最小增量。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>傳回值

滑塊在滑塊控制件上可以移動的最小增量。

## <a name="cmfcribbonslidergetregularsize"></a><a name="getregularsize"></a>CMFC 功能滑動器:取得一般大小

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcribbonslidergetzoomincrement"></a><a name="getzoomincrement"></a>CMFC 功能滑塊::取得放大增量

獲取滑塊控制的縮放增量。

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>傳回值

滑塊控制的縮放增量。

## <a name="cmfcribbonsliderhaszoombuttons"></a><a name="haszoombuttons"></a>CMFC 功能滑動器::有縮放按鈕

指定滑塊是否具有縮放按鈕。

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>傳回值

如果滑塊具有縮放按鈕,則為 TRUE;否則。

## <a name="cmfcribbonsliderondraw"></a><a name="ondraw"></a>CMFC剪綵器:在畫上

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcribbonslidersetpos"></a><a name="setpos"></a>CMFC 剪桿::設置Pos

設置滑塊控制的當前位置。

```cpp
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>參數

*nPos*<br/>
[在]指定要為滑塊設置的位置。 該位置相對於滑塊的開頭。

*bredraw*<br/>
[在]如果為 TRUE,則滑塊將重新繪製。

## <a name="cmfcribbonslidersetrange"></a><a name="setrange"></a>CMFC 剪桿滑塊::設定範圍

設置滑塊控制的值範圍。

```cpp
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>參數

*nMin*<br/>
[在]指定滑塊控制的最小值。

*nMax*<br/>
[在]指定滑塊控制項的最大值。

### <a name="remarks"></a>備註

通過設置最小值和最大值來指定滑塊控制項的值範圍。

## <a name="cmfcribbonslidersetzoombuttons"></a><a name="setzoombuttons"></a>CMFC 功能滑動器:設定縮放按鈕

顯示或隱藏縮放按鈕。

```cpp
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>參數

[在]。 *bSet*TRUE 以顯示縮放按鈕;假隱藏它們。

## <a name="cmfcribbonslidersetzoomincrement"></a><a name="setzoomincrement"></a>CMFC 功能滑塊::設定放大增量

設置滑塊控制的縮放增量。

```cpp
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>參數

*nZoom 增量*<br/>
[在]指定滑塊控制的縮放增量。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement 類別](../../mfc/reference/cmfcribbonbaseelement-class.md)
