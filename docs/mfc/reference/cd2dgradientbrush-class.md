---
title: CD2DGradientBrush 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
dev_langs:
- C++
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c01dbb3b14c13182afc85412b5c3ffa3ac0e9cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush 類別
CD2DLinearGradientBrush 和 CD2DRadialGradientBrush 類別的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DGradientBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|建構 CD2DGradientBrush 物件。|  
|[CD2DGradientBrush:: ~ CD2DGradientBrush](#cd2dgradientbrush__~cd2dgradientbrush)|解構函式。 D2D 漸層筆刷物件終結時呼叫。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGradientBrush::Destroy](#destroy)|CD2DGradientBrush 物件已遭終結。 (覆寫[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy)。)|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|D2D1_GRADIENT_STOP 結構的陣列。|  
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|在哪種色彩漸層停駐點之間的插補執行空間。|  
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|正規化 [0 1] 範圍以外的漸層的行為。|  
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|D2D1_GRADIENT_STOP 結構陣列的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DGradientBrush`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="_dtorcd2dgradientbrush"></a>  CD2DGradientBrush:: ~ CD2DGradientBrush  
 解構函式。 D2D 漸層筆刷物件終結時呼叫。  
  
```  
virtual ~CD2DGradientBrush();
```  
  
##  <a name="cd2dgradientbrush"></a>  CD2DGradientBrush::CD2DGradientBrush  
 建構 CD2DGradientBrush 物件。  
  
```  
CD2DGradientBrush(
    CRenderTarget* pParentTarget,  
    const D2D1_GRADIENT_STOP* gradientStops,  
    UINT gradientStopsCount,  
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
  
 `colorInterpolationGamma`  
 在哪種色彩漸層停駐點之間的插補執行空間。  
  
 `extendMode`  
 正規化 [0 1] 範圍以外的漸層的行為。  
  
 `pBrushProperties`  
 指標的不透明度和筆刷的轉換。  
  
 `bAutoDestroy`  
 表示擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="destroy"></a>  CD2DGradientBrush::Destroy  
 CD2DGradientBrush 物件已遭終結。  
  
```  
virtual void Destroy();
```  
  
##  <a name="m_argradientstops"></a>  CD2DGradientBrush::m_arGradientStops  
 D2D1_GRADIENT_STOP 結構的陣列。  
  
```  
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;  
```  
  
##  <a name="m_colorinterpolationgamma"></a>  CD2DGradientBrush::m_colorInterpolationGamma  
 在哪種色彩漸層停駐點之間的插補執行空間。  
  
```  
D2D1_GAMMA m_colorInterpolationGamma;  
```  
  
##  <a name="m_extendmode"></a>  CD2DGradientBrush::m_extendMode  
 正規化 [0 1] 範圍以外的漸層的行為。  
  
```  
D2D1_EXTEND_MODE m_extendMode;  
```  
  
##  <a name="m_pgradientstops"></a>  CD2DGradientBrush::m_pGradientStops  
 D2D1_GRADIENT_STOP 結構陣列的指標。  
  
```  
ID2D1GradientStopCollection* m_pGradientStops;  
```  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
