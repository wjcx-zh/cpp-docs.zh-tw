---
title: CD2DGeometrySink 類別 |Microsoft 文件
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
ms.openlocfilehash: b8c96e83d15110cb85e23cd7a8643d615cf7c0d8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952368"
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
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|建構來自 CD2DPathGeometry 物件 CD2DGeometrySink 物件。|  
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|解構函式。 D2D 幾何接收物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](#addarc)|將單一圓弧加入至之路徑幾何|  
|[CD2DGeometrySink::AddBezier](#addbezier)|在目前的點和指定的結束點之間建立三次方貝茲曲線。|  
|[CD2DGeometrySink::AddBeziers](#addbeziers)|建立三次方貝茲曲線的序列，並將它們加入至這個幾何接收器。|  
|[CD2DGeometrySink::AddLine](#addline)|建立目前點和指定的結束點之間的線段，並將它加入至這個幾何接收器。|  
|[CD2DGeometrySink::AddLines](#addlines)|建立使用指定的點線的序列，並將它們加入至這個幾何接收器。|  
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|在目前的點和指定的結束點之間建立二次方貝茲曲線。|  
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|將一連串的二次方貝茲區段，做為陣列的單一呼叫中。|  
|[CD2DGeometrySink::BeginFigure](#beginfigure)|開始新的圖形，在指定的點。|  
|[CD2DGeometrySink::Close](#close)|關閉幾何接收|  
|[CD2DGeometrySink::EndFigure](#endfigure)|結束目前的圖形。（選擇性） 就會關閉它。|  
|[CD2DGeometrySink::Get](#get)|傳回 ID2D1GeometrySink 介面|  
|[CD2DGeometrySink::IsValid](#isvalid)|檢查幾何接收有效性|  
|[CD2DGeometrySink::SetFillMode](#setfillmode)|指定用來判斷哪些資料夾位於此幾何接收器所描述的幾何點以及哪些是外部的點的方法。|  
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|指定要套用至新的區段加入至這個幾何接收器筆劃和聯結選項。|  
  
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
 解構函式。 D2D 幾何接收物件終結時呼叫。  
  
```  
virtual ~CD2DGeometrySink();
```  
  
##  <a name="addarc"></a>  CD2DGeometrySink::AddArc  
 將單一圓弧加入至之路徑幾何  
  
```  
void AddArc(const D2D1_ARC_SEGMENT& arc);
```  
  
### <a name="parameters"></a>參數  
 *弧線*  
 此圖中加入的圓弧線段  
  
##  <a name="addbezier"></a>  CD2DGeometrySink::AddBezier  
 在目前的點和指定的結束點之間建立三次方貝茲曲線。  
  
```  
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>參數  
 *貝茲*  
 結構描述的控點和結束點，若要加入的貝茲曲線。  
  
##  <a name="addbeziers"></a>  CD2DGeometrySink::AddBeziers  
 建立三次方貝茲曲線的序列，並將它們加入至這個幾何接收器。  
  
```  
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,  
    D2D1_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>參數  
 *「 環圈 」*  
 描述建立貝茲曲線的貝茲區段陣列。 從 geometry 接收的目前位置 （結束點繪製的最後一個區段或 BeginFigure 所指定的位置） 繪製曲線到陣列中的第一個貝茲區段的結束點。 如果陣列包含額外的貝茲區段，每個後續的貝茲區段會使用上述的貝茲區段的結束點做為其起始點。  
  
##  <a name="addline"></a>  CD2DGeometrySink::AddLine  
 建立目前點和指定的結束點之間的線段，並將它加入至這個幾何接收器。  
  
```  
void AddLine(CD2DPointF point);
```  
  
### <a name="parameters"></a>參數  
 *點*  
 若要繪製線條結束點。  
  
##  <a name="addlines"></a>  CD2DGeometrySink::AddLines  
 建立使用指定的點線的序列，並將它們加入至這個幾何接收器。  
  
```  
void AddLines(
    const CArray<CD2DPointF,  
    CD2DPointF>& points);
```  
  
### <a name="parameters"></a>參數  
 *點*  
 描述要繪製線條的一或多個點陣列。 線條會繪製幾何接收的目前點 （結束點繪製的最後一個區段或 BeginFigure 所指定的位置） 從陣列中的第一個點。 如果陣列包含額外的點，線條會繪製的第一個點從陣列中從第三個點，等第二個點的第二個點。 陣列的一連串的繪製線條的端點。  
  
##  <a name="addquadraticbezier"></a>  CD2DGeometrySink::AddQuadraticBezier  
 在目前的點和指定的結束點之間建立二次方貝茲曲線。  
  
```  
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```  
  
### <a name="parameters"></a>參數  
 *貝茲*  
 描述控制項控點和結束點的二次方貝茲曲線，若要加入的結構。  
  
##  <a name="addquadraticbeziers"></a>  CD2DGeometrySink::AddQuadraticBeziers  
 將一連串的二次方貝茲區段，做為陣列的單一呼叫中。  
  
```  
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,  
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```  
  
### <a name="parameters"></a>參數  
 *「 環圈 」*  
 陣列的一連串的二次方貝茲區段。  
  
##  <a name="beginfigure"></a>  CD2DGeometrySink::BeginFigure  
 開始新的圖形，在指定的點。  
  
```  
void BeginFigure(
    CD2DPointF startPoint,  
    D2D1_FIGURE_BEGIN figureBegin);
```  
  
### <a name="parameters"></a>參數  
 *startPoint*  
 要開始新的圖形點。  
  
 *figureBegin*  
 新的圖是否應中空或填滿。  
  
##  <a name="cd2dgeometrysink"></a>  CD2DGeometrySink::CD2DGeometrySink  
 建構來自 CD2DPathGeometry 物件 CD2DGeometrySink 物件。  
  
```  
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```  
  
### <a name="parameters"></a>參數  
 *pathGeometry*  
 CD2DPathGeometry 現有的物件。  
  
##  <a name="close"></a>  CD2DGeometrySink::Close  
 關閉幾何接收  
  
```  
BOOL Close();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零否則為 FALSE。  
  
##  <a name="endfigure"></a>  CD2DGeometrySink::EndFigure  
 結束目前的圖形。（選擇性） 就會關閉它。  
  
```  
void EndFigure(D2D1_FIGURE_END figureEnd);
```  
  
### <a name="parameters"></a>參數  
 *figureEnd*  
 值，指出是否已關閉目前的圖形。 如果已關閉此圖中，在目前點和 BeginFigure 所指定的開始點之間繪製線條。  
  
##  <a name="get"></a>  CD2DGeometrySink::Get  
 傳回 ID2D1GeometrySink 介面  
  
```  
ID2D1GeometrySink* Get();
```  
  
### <a name="return-value"></a>傳回值  
 ID2D1GeometrySink 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="isvalid"></a>  CD2DGeometrySink::IsValid  
 檢查幾何接收有效性  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果幾何接收有效，則為 TRUE否則為 FALSE。  
  
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
 ID2D1GeometrySink 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="setfillmode"></a>  CD2DGeometrySink::SetFillMode  
 指定用來判斷哪些資料夾位於此幾何接收器所描述的幾何點以及哪些是外部的點的方法。  
  
```  
void SetFillMode(D2D1_FILL_MODE fillMode);
```  
  
### <a name="parameters"></a>參數  
 *fillMode*  
 用來判斷指定的點是否為幾何之一部分的方法。  
  
##  <a name="setsegmentflags"></a>  CD2DGeometrySink::SetSegmentFlags  
 指定要套用至新的區段加入至這個幾何接收器筆劃和聯結選項。  
  
```  
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```  
  
### <a name="parameters"></a>參數  
 *vertexFlags*  
 要套用至新的區段加入至這個幾何接收器筆劃和聯結選項。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
