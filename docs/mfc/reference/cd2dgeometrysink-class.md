---
title: CD2DGeometrySink 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: cb51c7b11f75debece61105bf20a201b6eab80a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369231"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink 類別

ID2D1 幾何基克的包裝器。

## <a name="syntax"></a>語法

```
class CD2DGeometrySink;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D幾何結構::CD2D幾何基克](#cd2dgeometrysink)|從 CD2DPath幾何物件構造 CD2D 幾何基克物件。|
|[CD2D幾何基克:*CD2D幾何](#_dtorcd2dgeometrysink)|解構函式。 銷毀 D2D 幾何接收器物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D幾何結構::添加弧](#addarc)|向路徑幾何體新增單個圓弧|
|[CD2D幾何Sink::AddBezier](#addbezier)|在目前的點和指定的結束點之間建立三次方貝茲曲線。|
|[CD2D幾何結構::添加貝塞爾](#addbeziers)|創建立方貝塞爾曲線序列,並將它們添加到幾何接收器。|
|[CD2D幾何結構::新增線](#addline)|在當前點和指定端點之間創建線段,並將其添加到幾何接收器。|
|[CD2D幾何結構::新增線](#addlines)|使用指定的點創建一系列線,並將它們添加到幾何接收器。|
|[CD2D幾何結構::添加四面體貝塞爾](#addquadraticbezier)|在目前的點和指定的結束點之間建立二次方貝茲曲線。|
|[CD2D幾何結構::添加四面體貝塞爾](#addquadraticbeziers)|在單個調用中添加二次貝塞爾段序列作為陣列。|
|[CD2D幾何結構::開始圖](#beginfigure)|在指定點啟動新圖形。|
|[CD2D 幾何結構:關閉](#close)|關閉幾何接收器|
|[CD2D幾何結構::結束圖](#endfigure)|結束當前數位;可以選擇關閉它。|
|[CD2D幾何結構:取得](#get)|傳回 ID2D1 幾何基克介面|
|[CD2D幾何結構::有效](#isvalid)|檢查幾何接收器的有效性|
|[CD2D幾何結構::設定填充模式](#setfillmode)|指定用於確定哪些點位於此幾何接收器描述的幾何體內部以及外部點的方法。|
|[CD2D幾何結構::設定分段標誌](#setsegmentflags)|指定要應用於添加到幾何接收器的新線段的描邊和聯接選項。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D幾何基克::操作員 ID2D1 幾何基克*](#operator_id2d1geometrysink_star)|傳回 ID2D1 幾何基克介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D幾何:m_pSink](#m_psink)|指向 ID2D1 幾何基克的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CD2DGeometrySink`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2D幾何基克:*CD2D幾何

解構函式。 銷毀 D2D 幾何接收器物件時調用。

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2D幾何結構::添加弧

向路徑幾何體新增單個圓弧

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>參數

*弧*<br/>
要新增到圖形中的弧段

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2D幾何Sink::AddBezier

在目前的點和指定的結束點之間建立三次方貝茲曲線。

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>參數

*貝塞爾*<br/>
描述要添加的貝氏曲線的控制點和終點的結構。

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2D幾何結構::添加貝塞爾

創建立方貝塞爾曲線序列,並將它們添加到幾何接收器。

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>參數

*貝塞爾斯*<br/>
描述要創建的貝氏曲線的貝氏氏段陣列。 曲線從幾何匯的當前點(繪製的最後一個線點的終點或 BeginFigure 指定的位置)繪製到陣列中第一個貝塞爾段的終點。 如果陣列包含其他貝塞爾段,則每個後續貝塞爾段使用前一個貝塞爾段的端點作為其起始點。

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2D幾何結構::新增線

在當前點和指定端點之間創建線段,並將其添加到幾何接收器。

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>參數

*點*<br/>
要繪製的線的終點。

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2D幾何結構::新增線

使用指定的點創建一系列線,並將它們添加到幾何接收器。

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>參數

*點*<br/>
描述要繪製的線條的一個或多個點的陣列。 線從幾何匯的當前點(繪製的最後一個線點的終點或 BeginFigure 指定的位置)繪製到陣列中的第一個點。 如果陣列包含其他點,則從陣列中的第一個點繪製一條線到陣列中的第二個點,從第二個點到第三個點,等等。 要繪製的線端點的序列的陣列。

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2D幾何結構::添加四面體貝塞爾

在目前的點和指定的結束點之間建立二次方貝茲曲線。

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>參數

*貝塞爾*<br/>
描述要添加的控制點和二次貝塞爾曲線的端點的結構。

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2D幾何結構::添加四面體貝塞爾

在單個調用中添加二次貝塞爾段序列作為陣列。

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>參數

*貝塞爾斯*<br/>
二次貝塞爾段序列的陣列。

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2D幾何結構::開始圖

在指定點啟動新圖形。

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>參數

*startPoint*<br/>
開始新數位的點。

*圖*<br/>
新圖形是空心的還是填充的。

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2D幾何結構::CD2D幾何基克

從 CD2DPath幾何物件構造 CD2D 幾何基克物件。

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>參數

*路徑幾何*<br/>
現有的 CD2DPath 幾何物件。

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a>CD2D 幾何結構:關閉

關閉幾何接收器

```
BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功,則非零;否則 FALSE。

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2D幾何結構::結束圖

結束當前數位;可以選擇關閉它。

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>參數

*圖結束*<br/>
指示當前圖形是否關閉的值。 如果圖形閉合,則在當前點和 BeginFigure 指定的起始點之間繪製一條線。

## <a name="cd2dgeometrysinkget"></a><a name="get"></a>CD2D幾何結構:取得

傳回 ID2D1 幾何基克介面

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1GeometrySink 介面或 NULL 的指標。

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2D幾何結構::有效

檢查幾何接收器的有效性

```
BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果幾何接收器有效,則為 TRUE;如果幾何接收器有效,則為 TRUE。否則 FALSE。

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a>CD2D幾何:m_pSink

指向 ID2D1 幾何基克的指標。

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2D幾何基克::操作員 ID2D1 幾何基克*

傳回 ID2D1 幾何基克介面

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1GeometrySink 介面或 NULL 的指標。

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2D幾何結構::設定填充模式

指定用於確定哪些點位於此幾何接收器描述的幾何體內部以及外部點的方法。

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>參數

*填滿模式*<br/>
用於確定給定點是否為幾何體的一部分的方法。

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2D幾何結構::設定分段標誌

指定要應用於添加到幾何接收器的新線段的描邊和聯接選項。

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>參數

*頂點旗標*<br/>
要應用於添加到幾何接收器的新線段的描邊和聯接選項。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
