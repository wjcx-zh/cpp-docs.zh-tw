---
title: "CD2DGeometrySink 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CD2DGeometrySink
- CD2DGeometrySink
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometrySink class
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8a51d9475437ae460340d419a88bc46effa81f5f
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink 類別
ID2D1GeometrySink 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DGeometrySink;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|建構 CD2DGeometrySink 物件從 CD2DPathGeometry 物件。|  
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|解構函式。 D2D 幾何接收器物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|加入之路徑幾何中的單一弧形|  
|[CD2DGeometrySink::AddBezier](#addbezier)|建立目前點和指定的結束點之間的三次方貝茲曲線。|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|建立一系列三次方貝茲曲線，並將它們加入至幾何接收。|  
|[CD2DGeometrySink::AddLine](#addline)|建立目前點和指定的結束點之間的直線線段，並將它加入至幾何接收器。|  
|[CD2DGeometrySink::AddLines](#addlines)|建立使用指定的點線的序列，並將它們加入至幾何接收。|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|建立目前點和指定的結束點之間的二次方貝茲曲線。|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|將一系列二次方貝茲區段加入做為陣列的單一呼叫中。|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|開始新的圖形，在指定的點。|  
|[CD2DGeometrySink::Close](#close)|關閉幾何接收器|  
|[CD2DGeometrySink::EndFigure](#endfigure)|結束目前的圖表。（選擇性） 會關閉。|  
|[CD2DGeometrySink::Get](#get)|傳回 ID2D1GeometrySink 介面|  
|[CD2DGeometrySink::IsValid](#isvalid)|檢查幾何接收器有效性|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|指定用來判斷屬於這個幾何接收所描述的 geometry 內點與點以外的方法。|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|指定要套用至新的區段加入至幾何接收筆劃並加入選項。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink *](#operator_id2d1geometrysink_star)|傳回 ID2D1GeometrySink 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DGeometrySink::m_pSink](#m_psink)|ID2D1GeometrySink 指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CD2DGeometrySink`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="a-namedtorcd2dgeometrysinka--cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink:: ~ CD2DGeometrySink  
 解構函式。 D2D 幾何接收器物件終結時呼叫。  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="a-nameaddarca--cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2DGeometrySink::AddArc  
 加入之路徑幾何中的單一弧形  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>參數  
 `arc`  
 圖中加入此圓弧線段  
  
##  <a name="a-nameaddbeziera--cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2DGeometrySink::AddBezier  
 建立目前點和指定的結束點之間的三次方貝茲曲線。  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>參數  
 `bezier`  
 結構描述的控點和結束點將貝茲曲線。  
  
##  <a name="a-nameaddbeziersa--cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2DGeometrySink::AddBeziers  
 建立一系列三次方貝茲曲線，並將它們加入至幾何接收。  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>參數  
 `beziers`  
 描述建立貝茲曲線的貝茲片段陣列。 曲線取自幾何接收器目前點 （結束點繪製的最後一個區段或 BeginFigure 所指定的位置），到陣列中的第一個貝茲區段的結束點。 如果陣列包含額外的貝茲片段，每個後續的貝茲區段會使用上述的貝茲區段的結束點做為其起始點。  
  
##  <a name="a-nameaddlinea--cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2DGeometrySink::AddLine  
 建立目前點和指定的結束點之間的直線線段，並將它加入至幾何接收器。  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>參數  
 `point`  
 若要繪製線條的結束點。  
  
##  <a name="a-nameaddlinesa--cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2DGeometrySink::AddLines  
 建立使用指定的點線的序列，並將它們加入至幾何接收。  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>參數  
 `points`  
 描述要繪製線條的一或多個點的陣列。 陣列中的第一個點，一條線是取自幾何接收器目前點 （結束點繪製的最後一個區段或 BeginFigure 所指定的位置）。 如果陣列包含額外的連接點，線條繪製從第一個點到第二個點陣列中從第二個點到第三個點，依此類推。 要繪製線條的終點序列的陣列。  
  
##  <a name="a-nameaddquadraticbeziera--cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier  
 建立目前點和指定的結束點之間的二次方貝茲曲線。  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>參數  
 `bezier`  
 描述控制項控點和結束點的二次方貝茲曲線，若要新增的結構。  
  
##  <a name="a-nameaddquadraticbeziersa--cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers  
 將一系列二次方貝茲區段加入做為陣列的單一呼叫中。  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>參數  
 `beziers`  
 陣列的一系列二次方貝茲區段。  
  
##  <a name="a-namebeginfigurea--cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2DGeometrySink::BeginFigure  
 開始新的圖形，在指定的點。  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>參數  
 `startPoint`  
 要開始新的圖形點。  
  
 `figureBegin`  
 新的圖是否應空心或填滿。  
  
##  <a name="a-namecd2dgeometrysinka--cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink  
 建構 CD2DGeometrySink 物件從 CD2DPathGeometry 物件。  
  
```  
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```  
  
### <a name="parameters"></a>參數  
 `pathGeometry`  
 現有的 CD2DPathGeometry 物件。  
  
##  <a name="a-nameclosea--cd2dgeometrysinkclose"></a><a name="close"></a>CD2DGeometrySink::Close  
 關閉幾何接收器  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零否則為 FALSE。  
  
##  <a name="a-nameendfigurea--cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2DGeometrySink::EndFigure  
 結束目前的圖表。（選擇性） 會關閉。  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>參數  
 `figureEnd`  
 值，指出是否已關閉目前的圖形。 如果關閉此圖中，在目前點和 BeginFigure 所指定的開始點之間繪製線條。  
  
##  <a name="a-namegeta--cd2dgeometrysinkget"></a><a name="get"></a>CD2DGeometrySink::Get  
 傳回 ID2D1GeometrySink 介面  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1GeometrySink 介面的指標。  
  
##  <a name="a-nameisvalida--cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2DGeometrySink::IsValid  
 檢查幾何接收器有效性  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果幾何接收無效，則為 TRUE否則為 FALSE。  
  
##  <a name="a-namempsinka--cd2dgeometrysinkmpsink"></a><a name="m_psink"></a>CD2DGeometrySink::m_pSink  
 ID2D1GeometrySink 指標。  
  
```  
ID2D1GeometrySink* m_pSink;  
```  
  
##  <a name="a-nameoperatorid2d1geometrysinkstara--cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink *  
 傳回 ID2D1GeometrySink 介面  
  
```  
operator ID2D1GeometrySink*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1GeometrySink 介面的指標。  
  
##  <a name="a-namesetfillmodea--cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2DGeometrySink::SetFillMode  
 指定用來判斷屬於這個幾何接收所描述的 geometry 內點與點以外的方法。  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>參數  
 `fillMode`  
 用來判斷指定的點是幾何的一部分的方法。  
  
##  <a name="a-namesetsegmentflagsa--cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags  
 指定要套用至新的區段加入至幾何接收筆劃並加入選項。  
  
```  
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```  
  
### <a name="parameters"></a>參數  
 `vertexFlags`  
 要套用至新的區段加入至幾何接收筆劃並加入選項。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

