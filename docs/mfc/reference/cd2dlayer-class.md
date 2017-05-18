---
title: "CD2DLayer 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
dev_langs:
- C++
helpviewer_keywords:
- CD2DLayer class
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
caps.latest.revision: 18
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
ms.openlocfilehash: d0034c37da7fa61c10cf6c7662ba361de8313aa0
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dlayer-class"></a>CD2DLayer 類別
ID2D1Layer 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CD2DLayer::CD2DLayer](#cd2dlayer)|建構 CD2DLayer 物件。|  
|[CD2DLayer:: ~ CD2DLayer](#_dtorcd2dlayer)|解構函式。 D2D 圖層物件終結時呼叫。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DLayer::Attach](#attach)|會附加至現有的資源物件的介面|  
|[CD2DLayer::Create](#create)|建立 CD2DLayer。 (覆寫[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DLayer::Destroy](#destroy)|終結 CD2DLayer 物件。 (覆寫[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DLayer::Detach](#detach)|中斷連結物件中的資源介面|  
|[CD2DLayer::Get](#get)|傳回 ID2D1Layer 介面|  
|[CD2DLayer::GetSize](#getsize)|傳回與裝置無關的像素為單位的呈現目標大小|  
|[CD2DLayer::IsValid](#isvalid)|檢查資源的有效性 (覆寫[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DLayer::operator ID2D1Layer *](#operator_id2d1layer_star)|傳回 ID2D1Layer 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CD2DLayer::m_pLayer](#m_player)|儲存 ID2D1Layer 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DLayer`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dlayer"></a>CD2DLayer:: ~ CD2DLayer  
 解構函式。 D2D 圖層物件終結時呼叫。  
  
```  
virtual ~CD2DLayer();
```  
  
##  <a name="attach"></a>CD2DLayer::Attach  
 會附加至現有的資源物件的介面  
  
```  
void Attach(ID2D1Layer* pResource);
```  
  
### <a name="parameters"></a>參數  
 `pResource`  
 現有的資源介面。 不能是 NULL  
  
##  <a name="cd2dlayer"></a>CD2DLayer::CD2DLayer  
 建構 CD2DLayer 物件。  
  
```  
CD2DLayer(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pParentTarget`  
 呈現目標指標。  
  
 `bAutoDestroy`  
 指出由擁有者 (pParentTarget) 將會終結物件。  
  
##  <a name="create"></a>CD2DLayer::Create  
 建立 CD2DLayer。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>參數  
 `pRenderTarget`  
 呈現目標指標。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，它會傳回 S_OK。 否則，它會傳回 HRESULT 錯誤碼。  
  
##  <a name="destroy"></a>CD2DLayer::Destroy  
 終結 CD2DLayer 物件。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DLayer::Detach  
 中斷連結物件中的資源介面  
  
```  
ID2D1Layer* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的資源介面指標。  
  
##  <a name="get"></a>CD2DLayer::Get  
 傳回 ID2D1Layer 介面  
  
```  
ID2D1Layer* Get();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1Layer 介面的指標。  
  
##  <a name="getsize"></a>CD2DLayer::GetSize  
 傳回與裝置無關的像素為單位的呈現目標大小  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 與裝置無關的像素為單位的呈現目標的目前大小  
  
##  <a name="isvalid"></a>CD2DLayer::IsValid  
 檢查資源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資源無效，則為 TRUE否則為 FALSE。  
  
##  <a name="m_player"></a>CD2DLayer::m_pLayer  
 儲存 ID2D1Layer 物件的指標。  
  
```  
ID2D1Layer* m_pLayer;  
```  
  
##  <a name="operator_id2d1layer_star"></a>CD2DLayer::operator ID2D1Layer *  
 傳回 ID2D1Layer 介面  
  
```  
operator ID2D1Layer* ();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1Layer 介面的指標。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

