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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b9d8373bdf1cba1c57936dfb4d98c5401c80476
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|解構函式。 D2D 幾何物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGeometry::Attach](#attach)|將現有的資源物件的介面|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|結合這種幾何形狀與指定的幾何，並將結果儲存 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|描述這種幾何形狀與指定的幾何的交集。 使用指定的簡維容錯來進行比較。|  
|[CD2DGeometry::ComputeArea](#computearea)|計算之幾何的區域之後，它所指定的矩陣轉換和扁平化，使用指定的容錯。|  
|[CD2DGeometry::ComputeLength](#computelength)|即使每個區段以執行行計算之幾何的長度。|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|之後，它會計算點和正切函數的指定幾何距離向量所指定的矩陣轉換和扁平化，使用指定的容錯。|  
|[CD2DGeometry::Destroy](#destroy)|CD2DGeometry 物件已遭終結。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DGeometry::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|表示是由幾何填滿的區域是否包含指定指定的簡維容錯的指定的點。|  
|[CD2DGeometry::Get](#get)|傳回 ID2D1Geometry 介面|  
|[CD2DGeometry::GetBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|在擴展所指定的筆劃的寬度和樣式及所指定的矩陣轉換之後，請取得幾何的界限。|  
|[CD2DGeometry::IsValid](#isvalid)|檢查資源的有效性 (會覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DGeometry::Outline](#outline)|將結果寫入 ID2D1SimplifiedGeometrySink 並計算外框的幾何。|  
|[CD2DGeometry::Simplify](#simplify)|建立只包含線條和 （選擇性） 三次方貝茲曲線，並將結果寫入至 ID2D1SimplifiedGeometrySink 之幾何的簡化的版本。|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|判斷幾何筆劃是否包含指定指定的筆劃粗細、 樣式和轉換的指定的點。|  
|[CD2DGeometry::Tessellate](#tessellate)|建立一組順時針彎曲三角形，已使用指定的矩陣已轉換之後，將涵蓋幾何和扁平化，使用指定的容錯。|  
|[CD2DGeometry::Widen](#widen)|將 geometry 擴展所指定的筆觸，且用戶端之後，將結果寫入 ID2D1SimplifiedGeometrySink 所指定的矩陣轉換和扁平化，使用指定的容錯。|  
  
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
  
##  <a name="_dtorcd2dgeometry"></a>CD2DGeometry:: ~ CD2DGeometry  
 解構函式。 D2D 幾何物件終結時呼叫。  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>CD2DGeometry::Attach  
 將現有的資源物件的介面  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有資源的介面。 不能是 NULL  
  
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
 表示擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry  
 結合這種幾何形狀與指定的幾何，並將結果儲存 ID2D1SimplifiedGeometrySink。  
  
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
 要結合與這個執行個體的幾何。  
  
 `combineMode`  
 若要執行合併操作類型。  
  
 `inputGeometryTransform`  
 要套用至合併前 inputGeometry 轉換。  
  
 `geometrySink`  
 合併作業的結果。  
  
 `flatteningTolerance`  
 距離點的幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry  
 描述這種幾何形狀與指定的幾何的交集。 使用指定的簡維容錯來進行比較。  
  
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
 距離點的幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="computearea"></a>CD2DGeometry::ComputeArea  
 計算之幾何的區域之後，它所指定的矩陣轉換和扁平化，使用指定的容錯。  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `worldTransform`  
 要套用至這個幾何計算其區域之前的轉換。  
  
 `area`  
 此方法傳回時，包含這種幾何形狀之轉換的扁平化新版區域的指標。 您必須為此參數來配置儲存空間。  
  
 `flatteningTolerance`  
 距離點之幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="computelength"></a>CD2DGeometry::ComputeLength  
 即使每個區段以執行行計算之幾何的長度。  
  
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
 此方法傳回時，包含指標之幾何的長度。 已關閉的幾何，長度會包含隱含結尾區段。 您必須為此參數來配置儲存空間。  
  
 `flatteningTolerance`  
 距離點之幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength  
 之後，它會計算點和正切函數的指定幾何距離向量所指定的矩陣轉換和扁平化，使用指定的容錯。  
  
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
 沿著點和尋找的正切值的幾何距離。 如果這個距離較少然後 0，這個方法會計算幾何中的第一個點。 如果這個距離大於幾何的長度，此方法會計算幾何中的最後一個點。  
  
 `worldTransform`  
 在之前計算指定的點和正切函數套用至的幾何轉換。  
  
 `point`  
 指定沿著幾何距離位置。 如果是空的幾何，這個點會包含 NaN 作為其 x 和 y 值。  
  
 `unitTangentVector`  
 此方法傳回時，包含幾何的指定距離向量正切函數的指標。 此向量幾何是空的如果包含 NaN，因為它的 x 和 y 值。 您必須為此參數來配置儲存空間。  
  
 `flatteningTolerance`  
 距離點之幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="destroy"></a>CD2DGeometry::Destroy  
 CD2DGeometry 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DGeometry::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源的介面指標。  
  
##  <a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint  
 表示是由幾何填滿的區域是否包含指定指定的簡維容錯的指定的點。  
  
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
 要套用至之前的內含項目測試的幾何轉換。  
  
 `contains`  
 這個方法傳回時，包含 bool 值是由幾何填滿的區域包含點，則為 TRUE，否則為 FALSE。 您必須為此參數來配置儲存空間。  
  
 `flatteningTolerance`  
 數值的精確度，但它的精確幾何的路徑與路徑交集的計算。 填滿遺漏小於容錯點仍會視為內。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="get"></a>CD2DGeometry::Get  
 傳回 ID2D1Geometry 介面  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>傳回值  
 ID2D1Geometry 介面或如果尚未初始化物件為 NULL 指標。  
  
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
 若要擴展之幾何的繪製控制項外框量。  
  
 `strokeStyle`  
 筆觸可擴展幾何的樣式。  
  
 `worldTransform`  
 要套用到幾何，而且已圖案幾何幾何轉換之後的轉換。  
  
 `bounds`  
 這個方法傳回時，包含擴大幾何的範圍。 您必須為此參數來配置儲存空間。  
  
 `flatteningTolerance`  
 距離點的幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="isvalid"></a>CD2DGeometry::IsValid  
 檢查資源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源有效，則為 TRUE否則為 FALSE。  
  
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
 ID2D1Geometry 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="outline"></a>CD2DGeometry::Outline  
 將結果寫入 ID2D1SimplifiedGeometrySink 並計算外框的幾何。  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>參數  
 `worldTransform`  
 要套用至外框的幾何轉換。  
  
 `geometrySink`  
 附加的幾何轉換的大綱 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 距離點之幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
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
 值，指定簡化的 geometry 是否應該包含曲線。  
  
 `worldTransform`  
 要套用至簡單的幾何轉換。  
  
 `geometrySink`  
 簡化的幾何附加 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 距離點之幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint  
 判斷幾何筆劃是否包含指定指定的筆劃粗細、 樣式和轉換的指定的點。  
  
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
 要套用的筆劃粗細。  
  
 `strokeStyle`  
 套用至筆觸的樣式。  
  
 `worldTransform`  
 要套用至繪製幾何轉換。  
  
 `contains`  
 此方法傳回時，包含布林值的幾何筆觸包含指定的點; 如果設定為 TRUE否則為 FALSE。 您必須為此參數來配置儲存空間。  
  
 `flatteningTolerance`  
 數值的精確度，但它的精確幾何的路徑與路徑交集的計算。 遺漏筆劃小於容錯點仍會視為內。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="tessellate"></a>CD2DGeometry::Tessellate  
 建立一組順時針彎曲三角形，已使用指定的矩陣已轉換之後，將涵蓋幾何和扁平化，使用指定的容錯。  
  
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
 附加的目標鑲嵌 ID2D1TessellationSink。  
  
 `flatteningTolerance`  
 距離點之幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="widen"></a>CD2DGeometry::Widen  
 將 geometry 擴展所指定的筆觸，且用戶端之後，將結果寫入 ID2D1SimplifiedGeometrySink 所指定的矩陣轉換和扁平化，使用指定的容錯。  
  
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
 要擴展之幾何的數量。  
  
 `strokeStyle`  
 要套用至的幾何或為 NULL 的筆劃的端點樣式。  
  
 `worldTransform`  
 要套用到幾何擴展它之後的轉換。  
  
 `geometrySink`  
 附加擴大的幾何 ID2D1SimplifiedGeometrySink。  
  
 `flatteningTolerance`  
 距離點之幾何的多邊形近似值之間最大上限。 較小的值會產生更精確的結果，但會導致執行速度緩慢。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
