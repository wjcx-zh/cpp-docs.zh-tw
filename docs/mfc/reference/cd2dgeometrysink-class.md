---
title: CD2DGeometrySink 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b97bccbf9615c90292976839f841e4b2ffe6af9d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383803"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink 類別

ID2D1GeometrySink 包裝函式。

## <a name="syntax"></a>語法

```
class CD2DGeometrySink;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|建構 CD2DGeometrySink 物件從 CD2DPathGeometry 物件。|
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|解構函式。 D2D geometry 接收器物件正在被終結時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|將路徑幾何中的單一弧形|
|[CD2DGeometrySink::AddBezier](#addbezier)|在目前的點和指定的結束點之間建立三次方貝茲曲線。|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|建立的三次方貝茲曲線序列，並將它們新增至 geometry 接收。|
|[CD2DGeometrySink::AddLine](#addline)|建立目前的點和指定的結束點之間的直線線段，並將它新增至 geometry 接收。|
|[CD2DGeometrySink::AddLines](#addlines)|建立使用指定的點線的序列，並將它們新增至 geometry 接收。|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|在目前的點和指定的結束點之間建立二次方貝茲曲線。|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|做為陣列的單一呼叫中新增二次方貝茲線段的序列。|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|開始新的圖形，在指定的時間點。|
|[CD2DGeometrySink::Close](#close)|關閉幾何接收|
|[CD2DGeometrySink::EndFigure](#endfigure)|結束目前的圖表;（選擇性） 關閉它。|
|[CD2DGeometrySink::Get](#get)|傳回 ID2D1GeometrySink 介面|
|[CD2DGeometrySink::IsValid](#isvalid)|檢查幾何接收有效性|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|指定用來判斷這點位於這個幾何接收所描述的幾何和點以外的方法。|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|指定要套用至新的區段新增至 geometry 接收筆劃和聯結的選項。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|傳回 ID2D1GeometrySink 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|ID2D1GeometrySink 指標。|

## <a name="inheritance-hierarchy"></a>繼承階層

`CD2DGeometrySink`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="_dtorcd2dgeometrysink"></a>  CD2DGeometrySink:: ~ CD2DGeometrySink

解構函式。 D2D geometry 接收器物件正在被終結時呼叫。

```
virtual ~CD2DGeometrySink();
```

##  <a name="addarc"></a>  CD2DGeometrySink::AddArc

將路徑幾何中的單一弧形

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>參數

*弧形*<br/>
若要加入圖此圓弧線段

##  <a name="addbezier"></a>  CD2DGeometrySink::AddBezier

在目前的點和指定的結束點之間建立三次方貝茲曲線。

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>參數

*貝茲*<br/>
結構描述的控制點和結束點將貝茲曲線。

##  <a name="addbeziers"></a>  CD2DGeometrySink::AddBeziers

建立的三次方貝茲曲線序列，並將它們新增至 geometry 接收。

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>參數

*貝茲曲線*<br/>
描述建立貝茲曲線的貝茲區段陣列。 曲線至陣列中的第一個貝茲區段的結束點繪製從幾何接收的目前點 （結束點繪製的最後一個區段或 BeginFigure 所指定的位置）。 如果陣列包含額外的貝茲區段，每個後續的貝茲區段會使用上述的貝茲線段的結束點為其開始點。

##  <a name="addline"></a>  CD2DGeometrySink::AddLine

建立目前的點和指定的結束點之間的直線線段，並將它新增至 geometry 接收。

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>參數

*點*<br/>
若要繪製線條結束點。

##  <a name="addlines"></a>  CD2DGeometrySink::AddLines

建立使用指定的點線的序列，並將它們新增至 geometry 接收。

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>參數

*點*<br/>
描述要繪製線條的一或多個點的陣列。 一條線取自幾何接收目前的點 （結束點繪製的最後一個區段或 BeginFigure 所指定的位置） 中，陣列中的第一個點。 如果陣列包含額外的點，會一條線繪製的第一個點到第二個點陣列中從第二個點到第三個點，以此類推。 繪製線條的終點序列的陣列。

##  <a name="addquadraticbezier"></a>  CD2DGeometrySink::AddQuadraticBezier

在目前的點和指定的結束點之間建立二次方貝茲曲線。

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>參數

*貝茲*<br/>
結構描述的控制點和結束點的二次方貝茲曲線加入。

##  <a name="addquadraticbeziers"></a>  CD2DGeometrySink::AddQuadraticBeziers

做為陣列的單一呼叫中新增二次方貝茲線段的序列。

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>參數

*貝茲曲線*<br/>
陣列的二次方貝茲線段序列。

##  <a name="beginfigure"></a>  CD2DGeometrySink::BeginFigure

開始新的圖形，在指定的時間點。

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>參數

*startPoint*<br/>
要開始新的圖形點。

*figureBegin*<br/>
新的圖是否應空心或填滿。

##  <a name="cd2dgeometrysink"></a>  CD2DGeometrySink::CD2DGeometrySink

建構 CD2DGeometrySink 物件從 CD2DPathGeometry 物件。

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>參數

*pathGeometry*<br/>
CD2DPathGeometry 現有的物件。

##  <a name="close"></a>  CD2DGeometrySink::Close

關閉幾何接收

```
BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功則為非零否則為 FALSE。

##  <a name="endfigure"></a>  CD2DGeometrySink::EndFigure

結束目前的圖表;（選擇性） 關閉它。

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>參數

*figureEnd*<br/>
值，指出是否要關閉目前的圖形。 如果圖已關閉，目前的點與 BeginFigure 所指定的起始點之間繪製線條。

##  <a name="get"></a>  CD2DGeometrySink::Get

傳回 ID2D1GeometrySink 介面

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1GeometrySink 介面的指標。

##  <a name="isvalid"></a>  CD2DGeometrySink::IsValid

檢查幾何接收有效性

```
BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果幾何接收有效，則為 TRUE。否則為 FALSE。

##  <a name="m_psink"></a>  CD2DGeometrySink::m_pSink

ID2D1GeometrySink 指標。

```
ID2D1GeometrySink* m_pSink;
```

##  <a name="operator_id2d1geometrysink_star"></a>  CD2DGeometrySink::operator ID2D1GeometrySink *

傳回 ID2D1GeometrySink 介面

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1GeometrySink 介面的指標。

##  <a name="setfillmode"></a>  CD2DGeometrySink::SetFillMode

指定用來判斷這點位於這個幾何接收所描述的幾何和點以外的方法。

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>參數

*fillMode*<br/>
用來判斷指定的點是否為幾何的一部分的方法。

##  <a name="setsegmentflags"></a>  CD2DGeometrySink::SetSegmentFlags

指定要套用至新的區段新增至 geometry 接收筆劃和聯結的選項。

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>參數

*vertexFlags*<br/>
要套用至新的區段新增至幾何的筆劃和聯結選項接收。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
