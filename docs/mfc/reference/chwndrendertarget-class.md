---
title: "CHwndRenderTarget 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CHwndRenderTarget class
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
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
ms.openlocfilehash: 1af6795e89c995ba6b5a7b094f06b0aea776f561
ms.lasthandoff: 02/24/2017

---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget 類別
ID2D1HwndRenderTarget 包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CHwndRenderTarget : public CRenderTarget;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|建構從 HWND CHwndRenderTarget 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CHwndRenderTarget::Attach](#attach)|會附加至現有的呈現目標物件的介面|  
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|指出是否要阻擋此呈現目標相關聯的 HWND。|  
|[CHwndRenderTarget::Create](#create)|建立呈現目標與視窗相關聯|  
|[CHwndRenderTarget::Detach](#detach)|中斷連結物件中的呈現目標介面|  
|[CHwndRenderTarget::GetHwnd](#gethwnd)|傳回與此相關聯的 HWND 呈現目標。|  
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|傳回 ID2D1HwndRenderTarget 介面。|  
|[CHwndRenderTarget::ReCreate](#recreate)|重新建立呈現目標與視窗相關聯|  
|[CHwndRenderTarget::Resize](#resize)|變更為指定之像素大小的呈現目標大小|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget *](#operator_id2d1hwndrendertarget_star)|傳回 ID2D1HwndRenderTarget 介面。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|ID2D1HwndRenderTarget 物件的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
 [CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxrendertarget.h  
  
##  <a name="attach"></a>CHwndRenderTarget::Attach  
 會附加至現有的呈現目標物件的介面  
  
```  
void Attach(ID2D1HwndRenderTarget* pTarget);
```  
  
### <a name="parameters"></a>參數  
 `pTarget`  
 現有的呈現目標介面。 不能是 NULL  
  
##  <a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState  
 指出是否要阻擋此呈現目標相關聯的 HWND。  
  
```  
D2D1_WINDOW_STATE CheckWindowState() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，指出是否與此相關聯的 HWND 呈現目標會阻擋。  
  
##  <a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget  
 建構從 HWND CHwndRenderTarget 物件。  
  
```  
CHwndRenderTarget(HWND hwnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `hwnd`  
 這與相關聯的 HWND 呈現目標  
  
##  <a name="create"></a>CHwndRenderTarget::Create  
 建立呈現目標與視窗相關聯  
  
```  
BOOL Create(HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 這與相關聯的 HWND 呈現目標  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE  
  
##  <a name="detach"></a>CHwndRenderTarget::Detach  
 中斷連結物件中的呈現目標介面  
  
```  
ID2D1HwndRenderTarget* Detach();
```  
  
### <a name="return-value"></a>傳回值  
 中斷連結的指標會呈現目標的介面。  
  
##  <a name="gethwnd"></a>CHwndRenderTarget::GetHwnd  
 傳回與此相關聯的 HWND 呈現目標。  
  
```  
HWND GetHwnd() const;  
```  
  
### <a name="return-value"></a>傳回值  
 這與相關聯的 HWND 呈現目標。  
  
##  <a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget  
 傳回 ID2D1HwndRenderTarget 介面。  
  
```  
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```  
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1HwndRenderTarget 介面的指標。  
  
##  <a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget  
 ID2D1HwndRenderTarget 物件的指標。  
  
```  
ID2D1HwndRenderTarget* m_pHwndRenderTarget;  
```  
  
##  <a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::operator ID2D1HwndRenderTarget *  
 傳回 ID2D1HwndRenderTarget 介面。  
  
```  
operator ID2D1HwndRenderTarget*();
```   
  
### <a name="return-value"></a>傳回值  
 如果物件尚未初始化為 NULL 的 ID2D1HwndRenderTarget 介面的指標。  
  
##  <a name="recreate"></a>CHwndRenderTarget::ReCreate  
 重新建立呈現目標與視窗相關聯  
  
```  
BOOL ReCreate(HWND hWnd);
```  
  
### <a name="parameters"></a>參數  
 `hWnd`  
 這與相關聯的 HWND 呈現目標  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
##  <a name="resize"></a>CHwndRenderTarget::Resize  
 變更為指定之像素大小的呈現目標大小  
  
```  
BOOL Resize(const CD2DSizeU& size);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 新的呈現目標裝置像素為單位的大小  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)

