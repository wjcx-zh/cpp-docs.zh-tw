---
title: "CWindowImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CWindowImpl"
  - "ATL.CWindowImpl"
  - "CWindowImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindowImpl class"
  - "subclassing windows, ATL"
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CWindowImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供建立或子類別化視窗的方法。  
  
> [!IMPORTANT]
>  此類別及其成員無法用於在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
class TBase= CWindow,  
class TWinTraits= CControlWinTraits   
>  
class ATL_NO_VTABLE CWindowImpl :  
public CWindowImplBaseT< TBase, TWinTraits>  
```  
  
#### 參數  
 `T`  
 衍生自 `CWindowImpl` 、您新創的類別  
  
 *TBase*  
 類別的基底類別。  根據預設，基底類別是[CWindow](../../atl/reference/cwindow-class.md)。  
  
 `TWinTraits`  
 定義視窗樣式的[特性類別](../../atl/understanding-window-traits.md) 。  預設值為 `CControlWinTraits`。  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CWindowImpl::Create](../Topic/CWindowImpl::Create.md)|建立視窗。|  
  
### CWindowImplBaseT 方法  
  
|||  
|-|-|  
|[DefWindowProc](../Topic/CWindowImpl::DefWindowProc.md)|提供預設訊息處理。|  
|[GetCurrentMessage](../Topic/CWindowImpl::GetCurrentMessage.md)|傳回目前訊息。|  
|[GetWindowProc](../Topic/CWindowImpl::GetWindowProc.md)|傳回目前視窗程序。|  
|[OnFinalMessage](../Topic/CWindowImpl::OnFinalMessage.md)|在最後一則訊息接收之後呼叫 \(一般為 `WM_NCDESTROY`\)。|  
|[SubclassWindow](../Topic/CWindowImpl::SubclassWindow.md)|子類別化一個視窗。|  
|[UnsubclassWindow](../Topic/CWindowImpl::UnsubclassWindow.md)|還原先前的子類別視窗。|  
  
### 靜態方法  
  
|||  
|-|-|  
|[GetWndClassInfo](../Topic/CWindowImpl::GetWndClassInfo.md)|傳回 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)靜態執行個體，其處理視窗類別資訊。|  
|[WindowProc](../Topic/CWindowImpl::WindowProc.md)|處理傳送至視窗的訊息。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_pfnSuperWindowProc](../Topic/CWindowImpl::m_pfnSuperWindowProc.md)|指向視窗類別的原始視窗程序。|  
  
## 備註  
 您可以使用 `CWindowImpl` 建立視窗或子類別化現有視窗。 `CWindowImpl` 視窗程序使用訊息對應，將訊息導向至適當的處理常式。  
  
 `CWindowImpl::Create` 建立基於視窗類別資訊的視窗、其視窗類別資訊由 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)管理。  `CWindowImpl` 包含 [DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md) 巨集，其表示 `CWndClassInfo` 註冊新的視窗類別。  如果您想要 Superclass 現有視窗類別，請從 `CWindowImpl` 衍生您自己的類別，並包含 [DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md) 巨集。  在這種情況下， `CWndClassInfo` 註冊了根據現有的類別但使用 `CWindowImpl::WindowProc`的視窗類別。  例如：  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/CPP/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  由於 `CWndClassInfo` 只處理一個視窗類別的資訊，每個透過 `CWindowImpl` 執行個體所建立的視窗是以相同的視窗類別為基底。  
  
 `CWindowImpl` 也支援視窗子類別化。  `SubclassWindow` 方法附加 `CWindowImpl` 物件的現有視窗，並變更視窗程序至 `CWindowImpl::WindowProc`。  `CWindowImpl` 執行個體可以子類別化不同的視窗。  
  
> [!NOTE]
>  對於任何指定的 `CWindowImpl` 物件，請呼叫 **Create** 或 `SubclassWindow`。  不要對同一物件叫用兩種方法。  
  
 除了 `CWindowImpl`以外， ATL 提供 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 來建立包含另一個物件的視窗。  
  
 基底類別解構函式 \(~**CWindowImplRoot**\) 保證在終結物件之前移除視窗。  
  
 `CWindowImpl` 衍生自**CWindowImplBaseT**，其衍生自 **CWindowImplRoot**，其衍生自 **TBase** 和 [CMessageMap](../../atl/reference/cmessagemap-class.md)。  
  
|如需詳細資訊|請參閱|  
|------------|---------|  
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 裡的視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|  
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|  
  
## 繼承階層架構  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## 需求  
 **標題：** atlwin.h  
  
## 請參閱  
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)