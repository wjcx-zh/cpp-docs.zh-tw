---
title: "CContainedWindowT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CContainedWindow"
  - "CContainedWindowT"
  - "ATL.CContainedWindowT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CContainedWindow class"
  - "CContainedWindowT class"
  - "contained windows"
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CContainedWindowT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作在另一個物件內所包含的視窗。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class TBase= CWindow,  
class TWinTraits= CControlWinTraits   
>  
class CContainedWindowT :  
public TBase  
```  
  
#### 參數  
 *TBase*  
 您的新類別的基底類別。  預設基底類別是 `CWindow`。  
  
 `TWinTraits`  
 字元類別會定義自己的視窗的樣式。  預設值為 `CControlWinTraits`。  
  
> [!NOTE]
>  [CContainedWindow](../Topic/CContainedWindow.md) 是 `CContainedWindowT`的特製化。  如果您想要變更基底類別或特性，請直接使用 `CContainedWindowT` 。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CContainedWindowT::CContainedWindowT](../Topic/CContainedWindowT::CContainedWindowT.md)|建構函式。  初始化資料成員指定訊息對應的處理所包含之視窗的訊息。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CContainedWindowT::Create](../Topic/CContainedWindowT::Create.md)|建立視窗。|  
|[CContainedWindowT::DefWindowProc](../Topic/CContainedWindowT::DefWindowProc.md)|提供預設的訊息處理。|  
|[CContainedWindowT::GetCurrentMessage](../Topic/CContainedWindowT::GetCurrentMessage.md)|傳回目前的訊息。|  
|[CContainedWindowT::RegisterWndSuperclass](../Topic/CContainedWindowT::RegisterWndSuperclass.md)|註冊所包含之視窗的視窗類別。|  
|[CContainedWindowT::SubclassWindow](../Topic/CContainedWindowT::SubclassWindow.md)|子類別視窗。|  
|[CContainedWindowT::SwitchMessageMap](../Topic/CContainedWindowT::SwitchMessageMap.md)|變更訊息對應來處理所包含之視窗的訊息。|  
|[CContainedWindowT::UnsubclassWindow](../Topic/CContainedWindowT::UnsubclassWindow.md)|還原先前子視窗。|  
|[CContainedWindowT::WindowProc](../Topic/CContainedWindowT::WindowProc.md)|\(靜態\) 處理傳送至包含的視窗。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CContainedWindowT::m\_dwMsgMapID](../Topic/CContainedWindowT::m_dwMsgMapID.md)|識別訊息對應的處理所包含之視窗的訊息。|  
|[CContainedWindowT::m\_lpszClassName](../Topic/CContainedWindowT::m_lpszClassName.md)|指定新的視窗類別現有視窗類別的名稱。|  
|[CContainedWindowT::m\_pfnSuperWindowProc](../Topic/CContainedWindowT::m_pfnSuperWindowProc.md)|將視窗類別的原始視窗程序的點。|  
|[CContainedWindowT::m\_pObject](../Topic/CContainedWindowT::m_pObject.md)|要包含的物件。|  
  
## 備註  
 `CContainedWindowT` 實作在另一個物件內所包含的視窗。  `CContainedWindowT` 的視窗程序在 \[即時訊息中包含的物件使用訊息對應至適當的處理常式。  當 `CContainedWindowT` 建構物件時，您會指定應該使用的訊息對應。  
  
 `CContainedWindowT` 可讓您透過 superclassing 現有視窗類別建立新視窗。  **建立** 方法的第一個註冊根據現有的類別，但是使用 `CContainedWindowT::WindowProc`的視窗類別。  **建立** 接著會根據此新的視窗類別的視窗。  `CContainedWindowT` 每個執行個體的 Superclass 可以中不同的視窗類別。  
  
 `CContainedWindowT` 也支援子類別化的視窗。  `SubclassWindow` 方法附加現有 Windows  `CContainedWindowT` 物件並變更視窗程序加入至 `CContainedWindowT::WindowProc`。  `CContainedWindowT` 每個執行個體的子類別可以在中不同的視窗。  
  
> [!NOTE]
>  對於任何特定的 `CContainedWindowT` 物件，請呼叫 **建立** 或 `SubclassWindow`。  您不應該叫用相同物件的兩個方法。  
  
 當您在 ATL 專案精靈使用 **Add control based on** 選項時，精靈會自動將名稱 `CContainedWindowT` 資料成員加入至實作控制項的類別。  下列範例顯示所包含的視窗如何宣告:  
  
 [!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/CPP/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/CPP/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/CPP/ccontainedwindowt-class_3.h)]  
  
|如需詳細資訊|請參閱|  
|------------|---------|  
|建立控制項|[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)|  
|使用 ATL 中的視窗|[ATL 視窗類別](../../atl/atl-window-classes.md)|  
|ATL 專案精靈|[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)|  
|視窗|[視窗](http://msdn.microsoft.com/library/windows/desktop/ms632595) 和後續的主題。 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## 繼承階層架構  
 `TBase`  
  
 `CContainedWindowT`  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [CWindow Class](../../atl/reference/cwindow-class.md)   
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap Class](../../atl/reference/cmessagemap-class.md)   
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)