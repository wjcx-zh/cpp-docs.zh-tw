---
title: CD2DGeometry 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 4549b2e7981d5f8493ddf9f24477e75a94ddde8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405725"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry 類別

ID2D1Geometry 包裝函式。

## <a name="syntax"></a>語法

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|建構 CD2DGeometry 物件。|
|[CD2DGeometry::~CD2DGeometry](#_dtorcd2dgeometry)|解構函式。 D2D geometry 物件正在被終結時呼叫。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DGeometry::Attach](#attach)|將現有的資源物件的介面|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|結合這個幾何與所指定幾何，並將結果儲存在 ID2D1SimplifiedGeometrySink。|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|描述這個幾何與所指定的幾何的交集。 使用指定的簡維容錯來進行比較。|
|[CD2DGeometry::ComputeArea](#computearea)|之後，計算的幾何區域所指定的矩陣轉換，並簡維使用指定的容許誤差。|
|[CD2DGeometry::ComputeLength](#computelength)|如同每個區段已 unrolled 成一條線，請計算幾何的長度。|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|之後，會計算沿著幾何距離點和正切向量轉換所指定的矩陣及壓平合併使用指定的容許誤差。|
|[CD2DGeometry::Destroy](#destroy)|終結 CD2DGeometry 物件。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|
|[CD2DGeometry::Detach](#detach)|中斷連結物件中的資源介面|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|表示幾何的填滿的區域是否包含指定指定簡維的容許誤差的指定的點。|
|[CD2DGeometry::Get](#get)|傳回 ID2D1Geometry 介面|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|在擴展所指定的筆劃的寬度和樣式及所指定的矩陣轉換之後，請取得幾何的界限。|
|[CD2DGeometry::IsValid](#isvalid)|檢查資源的有效性 (會覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2DGeometry::Outline](#outline)|計算外框的幾何，並將結果寫入 ID2D1SimplifiedGeometrySink。|
|[CD2DGeometry::Simplify](#simplify)|建立只包含線條和 （選擇性） 三次方貝茲曲線，並將結果寫入至 ID2D1SimplifiedGeometrySink 之幾何的簡化的版本。|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|判斷幾何筆劃是否包含指定的點，提供指定的筆劃粗細、 樣式和轉換。|
|[CD2DGeometry::Tessellate](#tessellate)|建立一份涵蓋幾何之後轉換使用指定的矩陣及壓平合併使用指定的容許誤差的順時針彎曲三角形。|
|[CD2DGeometry::Widen](#widen)|將幾何擴展所指定的筆劃並將結果寫入 ID2D1SimplifiedGeometrySink 之後, 所指定的矩陣轉換，並簡維使用指定的容許誤差。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|傳回 ID2D1Geometry 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|ID2D1Geometry 指標。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="_dtorcd2dgeometry"></a>  CD2DGeometry:: ~ CD2DGeometry

解構函式。 D2D geometry 物件正在被終結時呼叫。

```
virtual ~CD2DGeometry();
```

##  <a name="attach"></a>  CD2DGeometry::Attach

將現有的資源物件的介面

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>參數

*pResource*<br/>
現有的資源介面。 不能是 NULL

##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry

建構 CD2DGeometry 物件。

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*pParentTarget*<br/>
到轉譯目標的指標。

*bAutoDestroy*<br/>
表示擁有者 (pParentTarget) 將會終結物件。

##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry

結合這個幾何與所指定幾何，並將結果儲存在 ID2D1SimplifiedGeometrySink。

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*inputGeometry*<br/>
要結合與這個執行個體的幾何。

*combineMode*<br/>
若要執行的合併作業的類型。

*inputGeometryTransform*<br/>
要套用至 inputGeometry 合併之前的轉換。

*geometrySink*<br/>
合併作業的結果。

*flatteningTolerance*<br/>
距離的幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry

描述這個幾何與所指定的幾何的交集。 使用指定的簡維容錯來進行比較。

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*inputGeometry*<br/>
要測試的幾何。

*inputGeometryTransform*<br/>
要套用至 inputGeometry 轉換。

*flatteningTolerance*<br/>
距離的幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="computearea"></a>  CD2DGeometry::ComputeArea

之後，計算的幾何區域所指定的矩陣轉換，並簡維使用指定的容許誤差。

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*worldTransform*<br/>
要計算其區域之前套用至這個幾何的轉換。

*area*<br/>
當這個方法傳回時，包含這個幾何的轉換扁平化版本的區域的指標。 您必須為此參數來配置儲存體。

*flatteningTolerance*<br/>
距離幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="computelength"></a>  CD2DGeometry::ComputeLength

如同每個區段已 unrolled 成一條線，請計算幾何的長度。

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*worldTransform*<br/>
要計算其長度之前套用至幾何的轉換。

*length*<br/>
當這個方法傳回時，包含幾何的長度的指標。 對於已關閉的幾何，長度會包含隱含的結尾區段。 您必須為此參數來配置儲存體。

*flatteningTolerance*<br/>
距離幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength

之後，會計算沿著幾何距離點和正切向量轉換所指定的矩陣及壓平合併使用指定的容許誤差。

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*length*<br/>
沿著點和要尋找的正切值的幾何距離。 如果這個距離很少然後 0，這個方法會計算幾何中的第一個點。 如果此距離大於幾何的長度，這個方法會計算幾何中的最後一個點。

*worldTransform*<br/>
要計算正切值與指定的點之前套用至幾何的轉換。

*point*<br/>
指定沿著幾何距離位置。 如果幾何是空的這點就會包含 NaN 作為其 x 和 y 值。

*unitTangentVector*<br/>
當這個方法傳回時，會包含正切向量，指定沿著幾何距離的指標。 如果幾何是空的則這個向量會包含 NaN 作為其 x 和 y 值。 您必須為此參數來配置儲存體。

*flatteningTolerance*<br/>
距離幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="destroy"></a>  CD2DGeometry::Destroy

終結 CD2DGeometry 物件。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DGeometry::Detach

中斷連結物件中的資源介面

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>傳回值

中斷連結的資源介面指標。

##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint

表示幾何的填滿的區域是否包含指定指定簡維的容許誤差的指定的點。

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*point*<br/>
要測試的點。

*worldTransform*<br/>
要套用至測試內含項目之前的幾何轉換。

*contains*<br/>
當這個方法傳回時，包含幾何的填滿的區域包含點，則為 TRUE 的 bool 值否則為 FALSE。 您必須為此參數來配置儲存體。

*flatteningTolerance*<br/>
數值的精確度，但它的精確的幾何路徑和路徑交集的計算。 在仍視為遺失小於一個容錯的填色的點。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="get"></a>  CD2DGeometry::Get

傳回 ID2D1Geometry 介面

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1Geometry 介面的指標。

##  <a name="getbounds"></a>  CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>參數

*worldTransform*<br/>
*bounds*

### <a name="return-value"></a>傳回值

##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds

在擴展所指定的筆劃的寬度和樣式及所指定的矩陣轉換之後，請取得幾何的界限。

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*strokeWidth*<br/>
用來擴展所繪製其外框的幾何數量。

*strokeStyle*<br/>
可擴展幾何筆劃的樣式。

*worldTransform*<br/>
要套用至幾何的幾何轉換之後，而且已將描邊的幾何轉換。

*bounds*<br/>
當這個方法傳回時，包含加寬的幾何的範圍。 您必須為此參數來配置儲存體。

*flatteningTolerance*<br/>
距離的幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="isvalid"></a>  CD2DGeometry::IsValid

檢查資源的有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源無效，則為 TRUE否則為 FALSE。

##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry

ID2D1Geometry 指標。

```
ID2D1Geometry* m_pGeometry;
```

##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::operator ID2D1Geometry *

傳回 ID2D1Geometry 介面

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1Geometry 介面的指標。

##  <a name="outline"></a>  CD2DGeometry::Outline

計算外框的幾何，並將結果寫入 ID2D1SimplifiedGeometrySink。

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*worldTransform*<br/>
要套用至幾何外框的轉換。

*geometrySink*<br/>
要附加的幾何轉換的外框 ID2D1SimplifiedGeometrySink。

*flatteningTolerance*<br/>
距離幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="simplify"></a>  CD2DGeometry::Simplify

建立只包含線條和 （選擇性） 三次方貝茲曲線，並將結果寫入至 ID2D1SimplifiedGeometrySink 之幾何的簡化的版本。

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*simplificationOption*<br/>
值，指定簡化的幾何是否應該包含曲線。

*worldTransform*<br/>
要套用至簡化的幾何轉換。

*geometrySink*<br/>
要附加的簡化的幾何 ID2D1SimplifiedGeometrySink。

*flatteningTolerance*<br/>
距離幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint

判斷幾何筆劃是否包含指定的點，提供指定的筆劃粗細、 樣式和轉換。

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*point*<br/>
用來測試內含項目的點。

*strokeWidth*<br/>
若要套用的筆劃粗細。

*strokeStyle*<br/>
要套用的樣式。

*worldTransform*<br/>
要套用至繪製幾何轉換。

*contains*<br/>
當這個方法傳回時，會包含布林值設定為 TRUE，如果幾何筆劃包含指定的點;否則為 FALSE。 您必須為此參數來配置儲存體。

*flatteningTolerance*<br/>
數值的精確度，但它的精確的幾何路徑和路徑交集的計算。 在仍視為遺失小於一個容錯的筆劃的點。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="tessellate"></a>  CD2DGeometry::Tessellate

建立一份涵蓋幾何之後轉換使用指定的矩陣及壓平合併使用指定的容許誤差的順時針彎曲三角形。

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*worldTransform*<br/>
要套用至這個幾何或 NULL 的轉換。

*tessellationSink*<br/>
要鑲嵌附加 ID2D1TessellationSink。

*flatteningTolerance*<br/>
距離幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="widen"></a>  CD2DGeometry::Widen

將幾何擴展所指定的筆劃並將結果寫入 ID2D1SimplifiedGeometrySink 之後, 所指定的矩陣轉換，並簡維使用指定的容許誤差。

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*strokeWidth*<br/>
用來擴大幾何數量。

*strokeStyle*<br/>
要套用至幾何，則為 NULL 的筆劃的樣式。

*worldTransform*<br/>
要套用至幾何後擴展它的轉換。

*geometrySink*<br/>
要附加的加寬的幾何 ID2D1SimplifiedGeometrySink。

*flatteningTolerance*<br/>
距離幾何多邊形近似法中的點之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
