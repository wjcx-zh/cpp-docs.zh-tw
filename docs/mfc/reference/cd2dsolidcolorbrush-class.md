---
title: "CD2DSolidColorBrush 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DSolidColorBrush class
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
caps.latest.revision: 16
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
ms.openlocfilehash: 5b6cbd6a6a5557f5ea23c0556a4b87011b510411
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush 類別
ID2D1SolidColorBrush 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DSolidColorBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|多載。 建構 CD2DSolidColorBrush 物件。|  
|[CD2DSolidColorBrush:: ~ CD2DSolidColorBrush](#cd2dsolidcolorbrush__~cd2dsolidcolorbrush)|解構函式。 D2D 實心筆刷物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSolidColorBrush::Attach](#attach)|會附加至現有的資源物件的介面|  
|[CD2DSolidColorBrush::Create](#create)|建立 CD2DSolidColorBrush。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DSolidColorBrush::Destroy](#destroy)|終結 CD2DSolidColorBrush 物件。 (覆寫[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy)。)|  
|[CD2DSolidColorBrush::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DSolidColorBrush::Get](#get)|傳回 ID2D1SolidColorBrush 介面|  
|[CD2DSolidColorBrush::GetColor](#getcolor)|擷取單色筆刷色彩|  
|[CD2DSolidColorBrush::SetColor](#setcolor)|指定此單色筆刷色彩|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|傳回 ID2D1SolidColorBrush 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|筆刷不透明的色彩。|  
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|儲存 ID2D1SolidColorBrush 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dsolidcolorbrush"></a>CD2DSolidColorBrush:: ~ CD2DSolidColorBrush  
 解構函式。 D2D 實心筆刷物件終結時呼叫。  
  
```  
virtual ~CD2DSolidColorBrush();
```  
  
##  <a name="attach"></a>CD2DSolidColorBrush::Attach  
 會附加至現有的資源物件的介面  
  
```  
void Attach(ID2D1SolidColorBrush* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有的資源介面。 不能是 NULL  
  
##  <a name="cd2dsolidcolorbrush"></a>CD2DSolidColorBrush::CD2DSolidColorBrush  
 建構 CD2DSolidColorBrush 物件。  
  
```  
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,  
    D2D1_COLOR_F color,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,  
    COLORREF color,  
    int nAlpha = 255,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `color`  
 筆刷色彩紅色、 綠色、 藍色及 alpha 值。  
  
 `pBrushProperties`  
 指標的不透明度和筆刷轉換。  
  
 `bAutoDestroy`  
 指出由擁有者 (pParentTarget) 將會終結物件。  
  
 `nAlpha`  
 筆刷色彩的不透明度。  
  
##  <a name="create"></a>CD2DSolidColorBrush::Create  
 建立 CD2DSolidColorBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>CD2DSolidColorBrush::Destroy  
 終結 CD2DSolidColorBrush 物件。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DSolidColorBrush::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1SolidColorBrush* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源介面指標。  
  
##  <a name="get"></a>CD2DSolidColorBrush::Get  
 傳回 ID2D1SolidColorBrush 介面  
  
```  
ID2D1SolidColorBrush* Get();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1SolidColorBrush 介面的指標。  
  
##  <a name="getcolor"></a>CD2DSolidColorBrush::GetColor  
 擷取單色筆刷色彩  
  
```  
D2D1_COLOR_F GetColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 這個單色筆刷色彩  
  
##  <a name="m_colorsolid"></a>CD2DSolidColorBrush::m_colorSolid  
 筆刷不透明的色彩。  
  
```  
D2D1_COLOR_F m_colorSolid;  
```  
  
##  <a name="m_psolidcolorbrush"></a>CD2DSolidColorBrush::m_pSolidColorBrush  
 儲存 ID2D1SolidColorBrush 物件的指標。  
  
```  
ID2D1SolidColorBrush* m_pSolidColorBrush;  
```  
  
##  <a name="operator_id2d1solidcolorbrush_star"></a>CD2DSolidColorBrush::operator ID2D1SolidColorBrush *  
 傳回 ID2D1SolidColorBrush 介面  
  
```  
operator ID2D1SolidColorBrush*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1SolidColorBrush 介面的指標。  
  
##  <a name="setcolor"></a>CD2DSolidColorBrush::SetColor  
 指定此單色筆刷色彩  
  
```  
void SetColor(D2D1_COLOR_F color);
```  
  
### <a name="parameters"></a>參數  
 `color`  
 這個單色筆刷色彩  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

