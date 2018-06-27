---
title: CD2DLinearGradientBrush 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61dc2134a2da6570c748cebbfc770b213863de04
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957243"
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush 類別
ID2D1LinearGradientBrush 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|建構 CD2DLinearGradientBrush 物件。|  
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|解構函式。 D2D 線性漸層筆刷物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::Attach](#attach)|將現有的資源物件的介面|  
|[CD2DLinearGradientBrush::Create](#create)|建立 CD2DLinearGradientBrush。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DLinearGradientBrush::Destroy](#destroy)|CD2DLinearGradientBrush 物件已遭終結。 (覆寫[CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy)。)|  
|[CD2DLinearGradientBrush::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DLinearGradientBrush::Get](#get)|傳回 ID2D1LinearGradientBrush 介面|  
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|擷取線性漸層的結束座標|  
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|擷取線性漸層的起始座標|  
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|筆刷的座標空間中設定線性漸層的結束座標|  
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|設定線性漸層筆刷的座標空間中的起始座標|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *](#operator_id2d1lineargradientbrush_star)|傳回 ID2D1LinearGradientBrush 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|開始和結束點的漸層。|  
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|ID2D1LinearGradientBrush 指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DLinearGradientBrush`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="_dtorcd2dlineargradientbrush"></a>  CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush  
 解構函式。 D2D 線性漸層筆刷物件終結時呼叫。  
  
```  
virtual ~CD2DLinearGradientBrush();
```  
  
##  <a name="attach"></a>  CD2DLinearGradientBrush::Attach  
 將現有的資源物件的介面  
  
```  
void Attach(ID2D1LinearGradientBrush* pResource);
```  
  
### <a name="parameters"></a>參數  
 *pResource*  
 現有資源的介面。 不能是 NULL  
  
##  <a name="cd2dlineargradientbrush"></a>  CD2DLinearGradientBrush::CD2DLinearGradientBrush  
 建構 CD2DLinearGradientBrush 物件。  
  
```  
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,  
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,  
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *pParentTarget*  
 呈現目標指標。  
  
 *gradientStops*  
 D2D1_GRADIENT_STOP 結構陣列的指標。  
  
 *gradientStopsCount*  
 值大於或等於 1，gradientStops 陣列中指定漸層停駐點的數目。  
  
 *LinearGradientBrushProperties*  
 開始和結束點的漸層。  
  
 *colorInterpolationGamma*  
 在哪種色彩漸層停駐點之間的插補執行空間。  
  
 *extendMode*  
 正規化 [0 1] 範圍以外的漸層的行為。  
  
 *pBrushProperties*  
 指標的不透明度和筆刷的轉換。  
  
 *bAutoDestroy*  
 表示擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="create"></a>  CD2DLinearGradientBrush::Create  
 建立 CD2DLinearGradientBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 *pRenderTarget*  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>  CD2DLinearGradientBrush::Destroy  
 CD2DLinearGradientBrush 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DLinearGradientBrush::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1LinearGradientBrush* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源的介面指標。  
  
##  <a name="get"></a>  CD2DLinearGradientBrush::Get  
 傳回 ID2D1LinearGradientBrush 介面  
  
```  
ID2D1LinearGradientBrush* Get();
```  
  
### <a name="return-value"></a>傳回值  
 ID2D1LinearGradientBrush 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="getendpoint"></a>  CD2DLinearGradientBrush::GetEndPoint  
 擷取線性漸層的結束座標  
  
```  
CD2DPointF GetEndPoint() const;  
```  
  
### <a name="return-value"></a>傳回值  
 線性漸層筆刷的座標空間中的結束二維座標  
  
##  <a name="getstartpoint"></a>  CD2DLinearGradientBrush::GetStartPoint  
 擷取線性漸層的起始座標  
  
```  
CD2DPointF GetStartPoint() const;  
```  
  
### <a name="return-value"></a>傳回值  
 線性漸層筆刷的座標空間中的起始二維座標  
  
##  <a name="m_lineargradientbrushproperties"></a>  CD2DLinearGradientBrush::m_LinearGradientBrushProperties  
 開始和結束點的漸層。  
  
```  
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;  
```  
  
##  <a name="m_plineargradientbrush"></a>  CD2DLinearGradientBrush::m_pLinearGradientBrush  
 ID2D1LinearGradientBrush 指標。  
  
```  
ID2D1LinearGradientBrush* m_pLinearGradientBrush;  
```  
  
##  <a name="operator_id2d1lineargradientbrush_star"></a>  CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush *  
 傳回 ID2D1LinearGradientBrush 介面  
  
```  
operator ID2D1LinearGradientBrush*();
```   
  
### <a name="return-value"></a>傳回值  
 ID2D1LinearGradientBrush 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="setendpoint"></a>  CD2DLinearGradientBrush::SetEndPoint  
 筆刷的座標空間中設定線性漸層的結束座標  
  
```  
void SetEndPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>參數  
 *點*  
 線性漸層筆刷的座標空間中的結束二維座標  
  
##  <a name="setstartpoint"></a>  CD2DLinearGradientBrush::SetStartPoint  
 設定線性漸層筆刷的座標空間中的起始座標  
  
```  
void SetStartPoint(CD2DPointF point);
```  
  
### <a name="parameters"></a>參數  
 *點*  
 線性漸層筆刷的座標空間中的起始二維座標  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
