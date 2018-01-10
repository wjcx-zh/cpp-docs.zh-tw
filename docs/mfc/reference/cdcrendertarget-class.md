---
title: "CDCRenderTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
dev_langs: C++
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 502c9d7cedf782c6ce23ebaf22d30c9b0e5e7409
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget 類別
ID2D1DCRenderTarget 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CDCRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|建構 CDCRenderTarget 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDCRenderTarget::Attach](#attach)|將現有的轉譯目標物件的介面|  
|[CDCRenderTarget::BindDC](#binddc)|將呈現目標，就會發出繪製命令之裝置內容繫結|  
|[CDCRenderTarget::Create](#create)|建立 CDCRenderTarget。|  
|[CDCRenderTarget::Detach](#detach)|中斷連結物件中的呈現目標介面|  
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|傳回 ID2D1DCRenderTarget 介面|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|傳回 ID2D1DCRenderTarget 介面|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|ID2D1DCRenderTarget 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxrendertarget.h  
  
##  <a name="attach"></a>CDCRenderTarget::Attach  
 將現有的轉譯目標物件的介面  
  
```  
void Attach(ID2D1DCRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>參數  
 `pTarget`  
 現有的轉譯目標介面。 不能是 NULL  
  
##  <a name="binddc"></a>CDCRenderTarget::BindDC  
 將呈現目標，就會發出繪製命令之裝置內容繫結  
  
```  
BOOL BindDC(
    const CDC& dc,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 `dc`  
 裝置內容的呈現目標發出繪製命令  
  
 `rect`  
 維度的裝置內容 (HDC) 呈現目標繫結至控制代碼  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget  
 建構 CDCRenderTarget 物件。  
  
```  
CDCRenderTarget();
```  
  
##  <a name="create"></a>CDCRenderTarget::Create  
 建立 CDCRenderTarget。  
  
```  
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```  
  
### <a name="parameters"></a>參數  
 `props`  
 轉譯模式、 像素格式、 遠端處理選項、 DPI 的詳細資訊，以及所需的硬體呈現的最小 DirectX 支援。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="detach"></a>CDCRenderTarget::Detach  
 中斷連結物件中的呈現目標介面  
  
```  
ID2D1DCRenderTarget* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的指標會呈現目標的介面。  
  
##  <a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget  
 傳回 ID2D1DCRenderTarget 介面  
  
```  
ID2D1DCRenderTarget* GetDCRenderTarget();
```  
  
### <a name="return-value"></a>傳回值  
 ID2D1DCRenderTarget 介面或如果尚未初始化物件為 NULL 指標。  
  
##  <a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget  
 ID2D1DCRenderTarget 物件的指標。  
  
```  
ID2D1DCRenderTarget* m_pDCRenderTarget;  
```  
  
##  <a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operator ID2D1DCRenderTarget *  
 傳回 ID2D1DCRenderTarget 介面  
  
```  
operator ID2D1DCRenderTarget*();
```   
  
### <a name="return-value"></a>傳回值  
 ID2D1DCRenderTarget 介面或如果尚未初始化物件為 NULL 指標。  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
