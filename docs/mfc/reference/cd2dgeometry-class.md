---
title: "CD2DGeometry 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometry class
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 948b2e2154259557e3a52c2045586cffce2a16f8
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dgeometry-class"></a>CD2DGeometry 類別
ID2D1Geometry 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DGeometry : public CD2DResource;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|建構 CD2DGeometry 物件。|  
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|解構函式。 D2D geometry 物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGeometry::Attach](#attach)|會附加至現有的資源物件的介面|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|結合這個幾何與指定的幾何，並將結果儲存在 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|描述這個幾何與所指定的幾何的交集。 使用指定的簡維容錯來進行比較。|  
|[CD2DGeometry::ComputeArea](#computearea)|計算幾何的區域之後，所指定的矩陣轉換和扁平化，使用指定的容錯。|  
|[CD2DGeometry::ComputeLength](#computelength)|計算幾何的長度，就像每個區段 unrolled 為資料行。|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|之後，會計算點和正切函數的指定幾何距離向量轉換指定的矩陣，並將扁平化，使用指定的容錯。|  
|[CD2DGeometry::Destroy](#destroy)|終結 CD2DGeometry 物件。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DGeometry::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|表示幾何的填滿的區域是否包含指定指定的簡維容錯的指定的點。|  
|[CD2DGeometry::Get](#get)|傳回 ID2D1Geometry 介面|  
|[CD2DGeometry::GetBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|在擴展所指定的筆劃的寬度和樣式及所指定的矩陣轉換之後，請取得幾何的界限。|  
|[CD2DGeometry::IsValid](#isvalid)|檢查資源的有效性 (覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DGeometry::Outline](#outline)|計算幾何的外框，並將結果寫入 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::Simplify](#simplify)|建立只包含線條和 （選擇性） 三次方貝茲曲線，並將結果寫入至 ID2D1SimplifiedGeometrySink 之幾何的簡化的版本。|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|判斷幾何筆劃是否包含指定的指定的筆觸粗細、 樣式和轉換指定的位置。|  
|[CD2DGeometry::Tessellate](#tessellate)|會建立一組順時針彎曲三角形，涵蓋幾何之後完成轉換使用指定的矩陣和扁平化，使用指定的容錯。|  
|[CD2DGeometry::Widen](#widen)|幾何擴展所指定的筆劃，並將結果寫入 ID2D1SimplifiedGeometrySink 之後，所指定的矩陣轉換和扁平化，使用指定的容錯。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
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
 **標頭︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dgeometry"></a>CD2DGeometry:: ~ CD2DGeometry  
 解構函式。 D2D geometry 物件終結時呼叫。  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>CD2DGeometry::Attach  
 會附加至現有的資源物件的介面  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有的資源介面。 不能是 NULL  
  
##  <a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry  
 建構 CD2DGeometry 物件。  
  
```  
CD2DGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `bAutoDestroy`  
 指出由擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry  
 結合這個幾何與指定的幾何，並將結果儲存在 ID2D1SimplifiedGeometrySink。  
  
```  
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,  
    D2D1_COMBINE_MODE combineMode,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `inputGeometry`  
 若要將這個執行個體與幾何。  
  
 `combineMode`  
 若要執行的合併作業的類型。  
  
 `inputGeometryTransform`  
 要套用至合併前 inputGeometry 轉換。  
  
 `geometrySink`  
 合併作業的結果。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry  
 描述這個幾何與所指定的幾何的交集。 使用指定的簡維容錯來進行比較。  
  
```  
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `inputGeometry`  
 要測試的幾何。  
  
 `inputGeometryTransform`  
 要套用至 inputGeometry 轉換。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="computearea"></a>CD2DGeometry::ComputeArea  
 計算幾何的區域之後，所指定的矩陣轉換和扁平化，使用指定的容錯。  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `worldTransform`  
 若要計算其區域之前套用至這個幾何轉換。  
  
 `area`  
 此方法傳回時，包含這個幾何轉換的簡維版的區域的指標。 這個參數，您必須配置儲存體。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="computelength"></a>CD2DGeometry::ComputeLength  
 計算幾何的長度，就像每個區段 unrolled 為資料行。  
  
```  
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& length,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `worldTransform`  
 要計算其長度之前套用至幾何轉換。  
  
 `length`  
 此方法傳回時，包含幾何的長度的指標。 已關閉的幾何長度包含隱含的結尾區段。 這個參數，您必須配置儲存體。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength  
 之後，會計算點和正切函數的指定幾何距離向量轉換指定的矩陣，並將扁平化，使用指定的容錯。  
  
```  
BOOL ComputePointAtLength(
    FLOAT length,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DPointF& point,  
    CD2DPointF& unitTangentVector,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `length`  
 沿著點和正切函數，若要尋找的幾何距離。 如果距離這麼少然後 0，則這個方法會計算幾何中的第一個點。 如果這個距離大於幾何的長度，則這個方法會計算幾何中的最後一個點。  
  
 `worldTransform`  
 要計算的指定的點和正切函數之前套用至幾何轉換。  
  
 `point`  
 指定沿著幾何距離位置。 如果幾何是空白，這個點都包含 NaN 作為其 x 和 y 值。  
  
 `unitTangentVector`  
 此方法傳回時，包含幾何的指定距離向量正切函數的指標。 如果幾何是空白，這個向量包含 NaN 其 x 和 y 值。 這個參數，您必須配置儲存體。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="destroy"></a>CD2DGeometry::Destroy  
 終結 CD2DGeometry 物件。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DGeometry::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源介面指標。  
  
##  <a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint  
 表示幾何的填滿的區域是否包含指定指定的簡維容錯的指定的點。  
  
```  
BOOL FillContainsPoint(
    CD2DPointF point,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `point`  
 要測試的點。  
  
 `worldTransform`  
 要套用至測試內含項目之前的幾何轉換。  
  
 `contains`  
 這個方法傳回時，包含 bool 值的幾何填滿的區域包含點，則為 TRUE，否則為 FALSE。 這個參數，您必須配置儲存體。  
  
 `flatteningTolerance`  
 數值的精確度，但其精確的幾何路徑和路徑交集的計算。 填滿遺漏小於容錯點仍會視為內。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="get"></a>CD2DGeometry::Get  
 傳回 ID2D1Geometry 介面  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1Geometry 介面的指標。  
  
##  <a name="getbounds"></a>CD2DGeometry::GetBounds  
  
```   
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,  
CD2DRectF& bounds) const; 
```  
  
### <a name="parameters"></a>參數  
 `worldTransform`  
 `bounds`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds  
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
 `strokeWidth`  
 若要將幾何擴大所繪製外框量。  
  
 `strokeStyle`  
 擴展幾何筆劃的樣式。  
  
 `worldTransform`  
 要套用至幾何，而且已圖案幾何幾何轉換之後的轉換。  
  
 `bounds`  
 這個方法傳回時，包含加寬幾何的範圍。 這個參數，您必須配置儲存體。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="isvalid"></a>CD2DGeometry::IsValid  
 檢查資源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源無效，則為 TRUE否則為 FALSE。  
  
##  <a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry  
 ID2D1Geometry 指標。  
  
```  
ID2D1Geometry* m_pGeometry;  
```  
  
##  <a name="operator_id2d1geometry_star"></a>CD2DGeometry::operator ID2D1Geometry *  
 傳回 ID2D1Geometry 介面  
  
```  
operator ID2D1Geometry*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1Geometry 介面的指標。  
  
##  <a name="outline"></a>CD2DGeometry::Outline  
 計算幾何的外框，並將結果寫入 ID2D1SimplifiedGeometrySink。  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `worldTransform`  
 要套用至外框幾何轉換。  
  
 `geometrySink`  
 要附加的幾何轉換的外框 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="simplify"></a>CD2DGeometry::Simplify  
 建立只包含線條和 （選擇性） 三次方貝茲曲線，並將結果寫入至 ID2D1SimplifiedGeometrySink 之幾何的簡化的版本。  
  
```  
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `simplificationOption`  
 值，指定是否包含簡化的幾何曲線。  
  
 `worldTransform`  
 要套用至簡單的幾何轉換。  
  
 `geometrySink`  
 要附加的簡化的幾何 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint  
 判斷幾何筆劃是否包含指定的指定的筆觸粗細、 樣式和轉換指定的位置。  
  
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
 `point`  
 若要測試的內含項目點。  
  
 `strokeWidth`  
 要套用筆觸粗細。  
  
 `strokeStyle`  
 若要套用筆劃的樣式。  
  
 `worldTransform`  
 要套用至描圖外的幾何轉換。  
  
 `contains`  
 此方法傳回時，會包含布林值設為 TRUE，如果幾何筆劃包含指定的點。否則為 FALSE。 這個參數，您必須配置儲存體。  
  
 `flatteningTolerance`  
 數值的精確度，但其精確的幾何路徑和路徑交集的計算。 遺漏筆劃小於容錯點仍會視為內。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="tessellate"></a>CD2DGeometry::Tessellate  
 會建立一組順時針彎曲三角形，涵蓋幾何之後完成轉換使用指定的矩陣和扁平化，使用指定的容錯。  
  
```  
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1TessellationSink* tessellationSink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `worldTransform`  
 要套用至這個幾何，則為 NULL 的轉換。  
  
 `tessellationSink`  
 要鑲嵌附加 ID2D1TessellationSink。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="widen"></a>CD2DGeometry::Widen  
 幾何擴展所指定的筆劃，並將結果寫入 ID2D1SimplifiedGeometrySink 之後，所指定的矩陣轉換和扁平化，使用指定的容錯。  
  
```  
BOOL Widen(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `strokeWidth`  
 用來擴展幾何數量。  
  
 `strokeStyle`  
 要套用至幾何，則為 NULL 的筆劃的樣式。  
  
 `worldTransform`  
 要擴大它之後套用至幾何轉換。  
  
 `geometrySink`  
 要附加加寬的幾何 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 距離點的幾何多邊形的近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

