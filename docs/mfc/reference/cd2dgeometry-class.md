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
ms.openlocfilehash: 4727f7b1799604001134ee2f4d2d2e1ce6db87fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754779"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry 類別

ID2D1 幾何體的包裝器。

## <a name="syntax"></a>語法

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 幾何:CD2D幾何](#cd2dgeometry)|構造 CD2D 幾何物件。|
|[CD2D幾何:*CD2D幾何](#_dtorcd2dgeometry)|解構函式。 銷毀 D2D 幾何物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D 幾何:附加](#attach)|將現有資源介面附加到物件|
|[CD2D幾何::與幾何體結合](#combinewithgeometry)|將此幾何體與指定的幾何體相結合,並將結果存儲在 ID2D1 簡化幾何結構中。|
|[CD2D幾何::與幾何體比較](#comparewithgeometry)|描述此幾何體和指定幾何體之間的交集。 比較使用指定的展平容差執行。|
|[CD2D 幾何:計算區域](#computearea)|計算幾何體的面積后,它已被指定的矩陣轉換,並使用指定的容差拼平。|
|[CD2D 幾何:計算長度](#computelength)|計算幾何的長度,就像每個線段都展開成一條線一樣。|
|[CD2D 幾何::計算點長度](#computepointatlength)|計算沿幾何體的指定距離的點和切線向量,然後由指定的矩陣轉換並使用指定的容差進行拼合。|
|[CD2D 幾何::D](#destroy)|銷毀 CD2D 幾何物件。 (覆蓋[CD2D 資源::D)](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2D 幾何::D](#detach)|從物件分離資源介面|
|[CD2D 幾何::填充包含點](#fillcontainspoint)|指示幾何圖形填充的區域是否包含給定指定平整容差的指定點。|
|[CD2D 幾何:取得](#get)|傳回 ID2D1 幾何介面|
|[CD2D 幾何:取得繫結](#getbounds)||
|[CD2D 幾何::獲取加束](#getwidenedbounds)|在幾何體被指定的描邊寬度和樣式加寬並由指定的矩陣轉換后獲取幾何體的邊界。|
|[CD2D 幾何:有效](#isvalid)|檢查資源有效性(覆寫[CD2D 資源::有效](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2D 幾何:大綱](#outline)|計算幾何體的輪廓並將結果寫入 ID2D1 簡化幾何結構。|
|[CD2D 幾何:簡化](#simplify)|創建僅包含線條和(可選)立方貝塞爾曲線的幾何圖形的簡化版本,並將結果寫入 ID2D1 簡化幾何結構。|
|[CD2D 幾何::筆劃包含點](#strokecontainspoint)|確定幾何體的描邊是否包含指定描邊厚度、樣式和變換的指定點。|
|[CD2D 幾何::底紋](#tessellate)|建立一組順時針彎曲的三角形，這組三角形在使用指定的矩陣轉換並且使用指定的容錯扁平化之後，將涵蓋幾何。|
|[CD2D 幾何:寬寬](#widen)|通過指定的描邊加寬幾何體,並將結果寫入 ID2D1SimplifiedGeometry Sink 後,該結果被指定的矩陣轉換並使用指定的容差進行拼合。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D幾何::操作員 ID2D1 幾何*](#operator_id2d1geometry_star)|傳回 ID2D1 幾何介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D 幾何::m_pGeometry](#m_pgeometry)|指向 ID2D1 幾何體的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a>CD2D幾何:*CD2D幾何

解構函式。 銷毀 D2D 幾何物件時調用。

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a>CD2D 幾何:附加

將現有資源介面附加到物件

```cpp
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a>CD2D 幾何:CD2D幾何

構造 CD2D 幾何物件。

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a>CD2D幾何::與幾何體結合

將此幾何體與指定的幾何體相結合,並將結果存儲在 ID2D1 簡化幾何結構中。

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*輸入幾何學*<br/>
要與此實例組合的幾何體。

*組合模式*<br/>
要執行的組合操作的類型。

*輸入幾何轉換*<br/>
要應用於輸入幾何的轉換,然後再合併。

*幾何結構*<br/>
合併操作的結果。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a>CD2D幾何::與幾何體比較

描述此幾何體和指定幾何體之間的交集。 比較使用指定的展平容差執行。

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*輸入幾何學*<br/>
要測試的幾何體。

*輸入幾何轉換*<br/>
應用於輸入幾何的轉換。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a>CD2D 幾何:計算區域

計算幾何體的面積后,它已被指定的矩陣轉換,並使用指定的容差拼平。

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*世界轉型*<br/>
在計算其面積之前應用於此幾何體的轉換。

*地區*<br/>
當此方法返回時,包含指向此幾何體的轉換的拼合版本的區域的指標。 您必須為此參數分配存儲。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a>CD2D 幾何:計算長度

計算幾何的長度,就像每個線段都展開成一條線一樣。

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*世界轉型*<br/>
在計算幾何體的長度之前應用於幾何體的變換。

*length*<br/>
當此方法返回時,包含指向幾何長度的指標。 對於閉合幾何體,長度包括隱式閉合段。 您必須為此參數分配存儲。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a>CD2D 幾何::計算點長度

計算沿幾何體的指定距離的點和切線向量,然後由指定的矩陣轉換並使用指定的容差進行拼合。

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
沿點的幾何體和要查找的切線的距離。 如果此距離小於 0,則此方法計算幾何體中的第一個點。 如果此距離大於幾何的長度,則此方法計算幾何體中的最後一個點。

*世界轉型*<br/>
在計算指定點和切線之前應用於幾何體的變換。

*點*<br/>
沿幾何圖形指定距離的位置。 如果幾何體為空,則此點包含 NaN 作為其 x 和 y 值。

*單位唐特向量*<br/>
當此方法返回時,包含指向沿幾何體指定距離的切線向量的指標。 如果幾何體為空,則此向量包含 NaN 作為其 x 和 y 值。 您必須為此參數分配存儲。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a>CD2D 幾何::D

銷毀 CD2D 幾何物件。

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a>CD2D 幾何::D

從物件分離資源介面

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a>CD2D 幾何::填充包含點

指示幾何圖形填充的區域是否包含給定指定平整容差的指定點。

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*點*<br/>
要測試的點。

*世界轉型*<br/>
在測試包含之前應用於幾何體的轉換。

*包含*<br/>
當此方法返回時,如果幾何圖形填充的區域包含點,則包含為 TRUE 的 bool 值;否則,FALSE。 您必須為此參數分配存儲。

*扁平公差*<br/>
計算精確幾何路徑和路徑交集的數位精度。 內仍考慮缺少小於容差的填充點。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometryget"></a><a name="get"></a>CD2D 幾何:取得

傳回 ID2D1 幾何介面

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1 幾何介面或 NULL 的指標。

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a>CD2D 幾何:取得繫結

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>參數

*世界轉型*<br/>
*邊界*

### <a name="return-value"></a>傳回值

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a>CD2D 幾何::獲取加束

在幾何體被指定的描邊寬度和樣式加寬並由指定的矩陣轉換后獲取幾何體的邊界。

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*筆劃寬度*<br/>
通過撫摸幾何輪廓來擴大幾何體的數量。

*筆劃樣式*<br/>
寬大幾何形狀的描邊樣式。

*世界轉型*<br/>
轉換幾何體后和幾何圖形描邊後應用於幾何圖形的變換。

*邊界*<br/>
當此方法返回時,包含加寬幾何體的邊界。 您必須為此參數分配存儲。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a>CD2D 幾何:有效

檢查資源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a>CD2D 幾何::m_pGeometry

指向 ID2D1 幾何體的指標。

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a>CD2D幾何::操作員 ID2D1 幾何*

傳回 ID2D1 幾何介面

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1 幾何介面或 NULL 的指標。

## <a name="cd2dgeometryoutline"></a><a name="outline"></a>CD2D 幾何:大綱

計算幾何體的輪廓並將結果寫入 ID2D1 簡化幾何結構。

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*世界轉型*<br/>
要應用於幾何輪廓的變換。

*幾何結構*<br/>
附加幾何體變換輪廓的 ID2D1 簡化幾何圖形。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a>CD2D 幾何:簡化

創建僅包含線條和(可選)立方貝塞爾曲線的幾何圖形的簡化版本,並將結果寫入 ID2D1 簡化幾何結構。

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*簡化選項*<br/>
指定簡化幾何圖形是否應包含曲線的值。

*世界轉型*<br/>
要應用於簡化幾何體的變換。

*幾何結構*<br/>
附加簡化幾何圖形的 ID2D1 簡化幾何圖形。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a>CD2D 幾何::筆劃包含點

確定幾何體的描邊是否包含指定描邊厚度、樣式和變換的指定點。

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

*點*<br/>
用來測試內含項目的點。

*筆劃寬度*<br/>
要應用的描邊的厚度。

*筆劃樣式*<br/>
要應用的筆畫樣式。

*世界轉型*<br/>
要應用於描邊幾何的變換。

*包含*<br/>
當此方法返回時,如果幾何體的描邊包含指定的點,則包含設置為 TRUE 的布爾值;否則,FALSE。 您必須為此參數分配存儲。

*扁平公差*<br/>
計算精確幾何路徑和路徑交集的數位精度。 內仍考慮以小於容差的筆劃點。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a>CD2D 幾何::底紋

建立一組順時針彎曲的三角形，這組三角形在使用指定的矩陣轉換並且使用指定的容錯扁平化之後，將涵蓋幾何。

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*世界轉型*<br/>
要應用於此幾何體或 NULL 的變換。

*鑲嵌*<br/>
附加鑲嵌的 ID2D1Tesssink。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cd2dgeometrywiden"></a><a name="widen"></a>CD2D 幾何:寬寬

通過指定的描邊加寬幾何體,並將結果寫入 ID2D1SimplifiedGeometry Sink 後,該結果被指定的矩陣轉換並使用指定的容差進行拼合。

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>參數

*筆劃寬度*<br/>
加寬幾何體的數量。

*筆劃樣式*<br/>
要應用於幾何體或 NULL 的描邊樣式。

*世界轉型*<br/>
在加寬幾何體后應用於幾何體的變換。

*幾何結構*<br/>
附加加寬幾何圖形的 ID2D1 簡化幾何圖形。

*扁平公差*<br/>
在幾何多邊形近似法中，點之間的距離上限。 值越小，產生的結果越精確，但執行過程也會比較慢。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
