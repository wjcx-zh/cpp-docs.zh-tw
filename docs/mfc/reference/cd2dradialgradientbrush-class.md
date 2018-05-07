---
title: CD2DRadialGradientBrush 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1be476c43b0752b95a6514057e240a030325b95d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush 類別
ID2D1RadialGradientBrush 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|建構 CD2DLinearGradientBrush 物件。|  
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|解構函式。 D2D 放射狀漸層筆刷物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::Attach](#attach)|將現有的資源物件的介面|  
|[CD2DRadialGradientBrush::Create](#create)|建立 CD2DRadialGradientBrush。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DRadialGradientBrush::Destroy](#destroy)|CD2DRadialGradientBrush 物件已遭終結。 (覆寫[CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy)。)|  
|[CD2DRadialGradientBrush::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DRadialGradientBrush::Get](#get)|傳回 ID2D1RadialGradientBrush 介面|  
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|擷取漸層停駐橢圓形的中心|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|擷取相對於漸層的橢圓形 center 漸層的原點位移|  
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|擷取漸層的橢圓形的 x 半徑|  
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|擷取漸層的橢圓形的 y 軸半徑|  
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|筆刷的座標空間中指定漸層停駐橢圓形的中心|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|指定相對於漸層的橢圓形 center 漸層的原點位移|  
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|指定漸層的橢圓形的 x 半徑筆刷的座標空間中|  
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|指定漸層的橢圓形的 y 軸半徑，筆刷的座標空間中|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|傳回 ID2D1RadialGradientBrush 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|ID2D1RadialGradientBrush 指標。|  
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|中心、 漸層的原點位移和半徑 x 和 y 半徑筆刷的漸層。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 `CD2DRadialGradientBrush`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="_dtorcd2dradialgradientbrush"></a>  CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush  
 解構函式。 D2D 放射狀漸層筆刷物件終結時呼叫。  
  
```  
virtual ~CD2DRadialGradientBrush();
```  
  
##  <a name="attach"></a>  CD2DRadialGradientBrush::Attach  
 將現有的資源物件的介面  
  
```  
void Attach(ID2D1RadialGradientBrush* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有資源的介面。 不能是 NULL  
  
##  <a name="cd2dradialgradientbrush"></a>  CD2DRadialGradientBrush::CD2DRadialGradientBrush  
 建構 CD2DLinearGradientBrush 物件。  
  
```  
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,  
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,  
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `gradientStops`  
 D2D1_GRADIENT_STOP 結構陣列的指標。  
  
 `gradientStopsCount`  
 值大於或等於 1，gradientStops 陣列中指定漸層停駐點的數目。  
  
 `RadialGradientBrushProperties`  
 中心、 漸層的原點位移和半徑 x 和 y 半徑筆刷的漸層。  
  
 `colorInterpolationGamma`  
 在哪種色彩漸層停駐點之間的插補執行空間。  
  
 `extendMode`  
 正規化 [0 1] 範圍以外的漸層的行為。  
  
 `pBrushProperties`  
 指標的不透明度和筆刷的轉換。  
  
 `bAutoDestroy`  
 表示擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="create"></a>  CD2DRadialGradientBrush::Create  
 建立 CD2DRadialGradientBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>  CD2DRadialGradientBrush::Destroy  
 CD2DRadialGradientBrush 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DRadialGradientBrush::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1RadialGradientBrush* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源的介面指標。  
  
##  <a name="get"></a>  CD2DRadialGradientBrush::Get  
 傳回 ID2D1RadialGradientBrush 介面  
  
```  
ID2D1RadialGradientBrush* Get();
```  
  
### <a name="return-value"></a>傳回值  
 ID2D1RadialGradientBrush 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="getcenter"></a>  CD2DRadialGradientBrush::GetCenter  
 擷取漸層停駐橢圓形的中心  
  
```  
CD2DPointF GetCenter() const;  
```  
  
### <a name="return-value"></a>傳回值  
 漸層的橢圓形的中心。 這個值表示筆刷的座標空間中  
  
##  <a name="getgradientoriginoffset"></a>  CD2DRadialGradientBrush::GetGradientOriginOffset  
 擷取相對於漸層的橢圓形 center 漸層的原點位移  
  
```  
CD2DPointF GetGradientOriginOffset() const;  
```  
  
### <a name="return-value"></a>傳回值  
 從中央漸層的橢圓形的漸層的原點位移。 這個值表示筆刷的座標空間中  
  
##  <a name="getradiusx"></a>  CD2DRadialGradientBrush::GetRadiusX  
 擷取漸層的橢圓形的 x 半徑  
  
```  
FLOAT GetRadiusX() const;  
```  
  
### <a name="return-value"></a>傳回值  
 漸層的橢圓形的 x 半徑。 這個值表示筆刷的座標空間中  
  
##  <a name="getradiusy"></a>  CD2DRadialGradientBrush::GetRadiusY  
 擷取漸層的橢圓形的 y 軸半徑  
  
```  
FLOAT GetRadiusY() const;  
```  
  
### <a name="return-value"></a>傳回值  
 漸層的橢圓形的 y 半徑。 這個值表示筆刷的座標空間中  
  
##  <a name="m_pradialgradientbrush"></a>  CD2DRadialGradientBrush::m_pRadialGradientBrush  
 ID2D1RadialGradientBrush 指標。  
  
```  
ID2D1RadialGradientBrush* m_pRadialGradientBrush;  
```  
  
##  <a name="m_radialgradientbrushproperties"></a>  CD2DRadialGradientBrush::m_RadialGradientBrushProperties  
 中心、 漸層的原點位移和半徑 x 和 y 半徑筆刷的漸層。  
  
```  
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;  
```  
  
##  <a name="operator_id2d1radialgradientbrush_star"></a>  CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *  
 傳回 ID2D1RadialGradientBrush 介面  
  
```  
operator ID2D1RadialGradientBrush*();
```   
  
### <a name="return-value"></a>傳回值  
 ID2D1RadialGradientBrush 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="setcenter"></a>  CD2DRadialGradientBrush::SetCenter  
 筆刷的座標空間中指定漸層停駐橢圓形的中心  
  
```  
void SetCenter(CD2DPointF point);
```  
  
### <a name="parameters"></a>參數  
 `point`  
 漸層停駐橢圓形，筆刷的座標空間中的中心  
  
##  <a name="setgradientoriginoffset"></a>  CD2DRadialGradientBrush::SetGradientOriginOffset  
 指定相對於漸層的橢圓形 center 漸層的原點位移  
  
```  
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```  
  
### <a name="parameters"></a>參數  
 `gradientOriginOffset`  
 漸層中心漸層的橢圓形的原點位移  
  
##  <a name="setradiusx"></a>  CD2DRadialGradientBrush::SetRadiusX  
 指定漸層的橢圓形的 x 半徑筆刷的座標空間中  
  
```  
void SetRadiusX(FLOAT radiusX);
```  
  
### <a name="parameters"></a>參數  
 `radiusX`  
 漸層的橢圓形的 x 半徑。 此值為筆刷的座標空間  
  
##  <a name="setradiusy"></a>  CD2DRadialGradientBrush::SetRadiusY  
 指定漸層的橢圓形的 y 軸半徑，筆刷的座標空間中  
  
```  
void SetRadiusY(FLOAT radiusY);
```  
  
### <a name="parameters"></a>參數  
 `radiusY`  
 漸層的橢圓形的 y 半徑。 此值為筆刷的座標空間  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
