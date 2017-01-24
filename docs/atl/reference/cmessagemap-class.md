---
title: "CMessageMap Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMessageMap"
  - "ATL.CMessageMap"
  - "ATL::CMessageMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 訊息處理常式"
  - "CMessageMap class"
  - "message maps, ATL"
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMessageMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別允許物件的訊息對應會存取由其他物件。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class ATL_NO_VTABLE CMessageMap  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMessageMap::ProcessWindowMessage](../Topic/CMessageMap::ProcessWindowMessage.md)|存取在 `CMessageMap`的訊息對應的衍生類別。|  
  
## 備註  
 `CMessageMap` 是允許物件的訊息對應由其他物件存取的抽象基底類別。  可以讓物件公開其訊息對應，它的類別必須繼承 `CMessageMap`衍生。  
  
 ATL 會 `CMessageMap` 支援內含的視窗和動態訊息對應繫結。  例如，其中任一個包含 [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) 物件類別必須從 `CMessageMap`衍生。  下列程式碼。 [SUBEDIT](../../top/visual-cpp-samples.md) 取樣。  藉由 [CComControl](../../atl/reference/ccomcontrol-class.md)， `CAtlEdit` 類別從 `CMessageMap`自動取得。  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/CPP/cmessagemap-class_1.h)]  
  
 因為包含的視窗， `m_EditCtrl`，包含在中的類別會使用訊息對應， `CAtlEdit``CMessageMap`從衍生。  
  
 如需訊息對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md) 本文「ATL 視窗類別上」。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [CDynamicChain Class](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)