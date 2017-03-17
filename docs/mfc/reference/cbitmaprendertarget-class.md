---
title: "CBitmapRenderTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CBitmapRenderTarget class
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 11bea138185df23c9f3cc79491c71d86861a6bdc
ms.lasthandoff: 02/24/2017

---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget 類別
ID2D1BitmapRenderTarget 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CBitmapRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|建構 CBitmapRenderTarget 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CBitmapRenderTarget::Attach](#attach)|會附加至現有的呈現目標物件的介面|  
|[CBitmapRenderTarget::Detach](#detach)|中斷連結物件中的呈現目標介面|  
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|擷取此呈現目標的點陣圖。 傳回的點陣圖用於繪製作業。|  
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|傳回 ID2D1BitmapRenderTarget 介面|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|傳回 ID2D1BitmapRenderTarget 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|ID2D1BitmapRenderTarget 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 `CBitmapRenderTarget` 
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="attach"></a>CBitmapRenderTarget::Attach  
 會附加至現有的呈現目標物件的介面  
  
```  
void Attach(ID2D1BitmapRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>參數  
 `pTarget`  
 現有的呈現目標介面。 不能是 NULL  
  
##  <a name="cbitmaprendertarget"></a>CBitmapRenderTarget::CBitmapRenderTarget  
 建構 CBitmapRenderTarget 物件。  
  
```  
CBitmapRenderTarget();
```  
  
##  <a name="detach"></a>CBitmapRenderTarget::Detach  
 中斷連結物件中的呈現目標介面  
  
```  
ID2D1BitmapRenderTarget* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的指標會呈現目標的介面。  
  
##  <a name="getbitmap"></a>CBitmapRenderTarget::GetBitmap  
 擷取此呈現目標的點陣圖。 傳回的點陣圖用於繪製作業。  
  
```  
BOOL GetBitmap(CD2DBitmap& bitmap);
```  
  
### <a name="parameters"></a>參數  
 `bitmap`  
 這個方法傳回時，包含此呈現目標的有效點陣圖。 此點陣圖用於繪製作業。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="getbitmaprendertarget"></a>CBitmapRenderTarget::GetBitmapRenderTarget  
 傳回 ID2D1BitmapRenderTarget 介面  
  
```  
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1BitmapRenderTarget 介面的指標。  
  
##  <a name="m_pbitmaprendertarget"></a>CBitmapRenderTarget::m_pBitmapRenderTarget  
 ID2D1BitmapRenderTarget 物件的指標。  
  
```  
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;  
```  
  
##  <a name="operator_id2d1bitmaprendertarget_star"></a>CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *  
 傳回 ID2D1BitmapRenderTarget 介面  
  
```  
operator ID2D1BitmapRenderTarget*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1BitmapRenderTarget 介面的指標。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

