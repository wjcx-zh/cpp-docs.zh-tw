---
title: "CDCRenderTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxrendertarget/CDCRenderTarget
- CDCRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CDCRenderTarget class
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2bbd62b06f4287904fce49f8a6ce9900476b07c0
ms.lasthandoff: 02/24/2017

---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget 類別
ID2D1DCRenderTarget 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|建構 CDCRenderTarget 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](#attach)|會附加至現有的呈現目標物件的介面|  
|[CDCRenderTarget::BindDC](#binddc)|將呈現目標繫結到它所簽發繪製命令的裝置內容|  
|[CDCRenderTarget::Create](#create)|建立 CDCRenderTarget。|  
|[CDCRenderTarget::Detach](#detach)|中斷連結物件中的呈現目標介面|  
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|傳回 ID2D1DCRenderTarget 介面|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|傳回 ID2D1DCRenderTarget 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|ID2D1DCRenderTarget 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="a-nameattacha--cdcrendertargetattach"></a><a name="attach"></a>CDCRenderTarget::Attach  
 會附加至現有的呈現目標物件的介面  
  
```  
void Attach(ID2D1DCRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>參數  
 `pTarget`  
 現有的呈現目標介面。 不能是 NULL  
  
##  <a name="a-namebinddca--cdcrendertargetbinddc"></a><a name="binddc"></a>CDCRenderTarget::BindDC  
 將呈現目標繫結到它所簽發繪製命令的裝置內容  
  
```  
BOOL BindDC(
    const CDC& dc,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `dc`  
 呈現目標問題繪製命令的裝置內容  
  
 `rect`  
 維度的呈現目標會繫結的裝置內容 (HDC) 的控制代碼  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="a-namecdcrendertargeta--cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget  
 建構 CDCRenderTarget 物件。  
  
```  
CDCRenderTarget();
```  
  
##  <a name="a-namecreatea--cdcrendertargetcreate"></a><a name="create"></a>CDCRenderTarget::Create  
 建立 CDCRenderTarget。  
  
```  
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```  
  
### <a name="parameters"></a>參數  
 `props`  
 轉譯模式、 像素格式、 遠端處理選項、 DPI 的詳細資訊，以及硬體呈現所需的最小 DirectX 支援。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="a-namedetacha--cdcrendertargetdetach"></a><a name="detach"></a>CDCRenderTarget::Detach  
 中斷連結物件中的呈現目標介面  
  
```  
ID2D1DCRenderTarget* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的指標會呈現目標的介面。  
  
##  <a name="a-namegetdcrendertargeta--cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget  
 傳回 ID2D1DCRenderTarget 介面  
  
```  
ID2D1DCRenderTarget* GetDCRenderTarget();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1DCRenderTarget 介面的指標。  
  
##  <a name="a-namempdcrendertargeta--cdcrendertargetmpdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget  
 ID2D1DCRenderTarget 物件的指標。  
  
```  
ID2D1DCRenderTarget* m_pDCRenderTarget;  
```  
  
##  <a name="a-nameoperatorid2d1dcrendertargetstara--cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operator ID2D1DCRenderTarget *  
 傳回 ID2D1DCRenderTarget 介面  
  
```  
operator ID2D1DCRenderTarget*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1DCRenderTarget 介面的指標。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

