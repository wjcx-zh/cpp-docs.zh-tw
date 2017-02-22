---
title: "CDynamicChain Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CDynamicChain"
  - "ATL.CDynamicChain"
  - "CDynamicChain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicChain class"
  - "chaining message maps"
  - "message maps, 鏈結"
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDynamicChain Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供支援動態繫結訊息對應的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CDynamicChain  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDynamicChain::CDynamicChain](../Topic/CDynamicChain::CDynamicChain.md)|建構函式。|  
|[CDynamicChain::~CDynamicChain](../Topic/CDynamicChain::~CDynamicChain.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDynamicChain::CallChain](../Topic/CDynamicChain::CallChain.md)|指示視窗訊息至另一個物件的訊息對應。|  
|[CDynamicChain::RemoveChainEntry](../Topic/CDynamicChain::RemoveChainEntry.md)|從集合中移除的訊息對應項目。|  
|[CDynamicChain::SetChainEntry](../Topic/CDynamicChain::SetChainEntry.md)|加入訊息對應項目加入至集合或修改現有的項目。|  
  
## 備註  
 `CDynamicChain` 處理訊息對應的集合，可讓 Windows 訊息導向，在執行階段，加入另一個物件的訊息對應。  
  
 若要支援動態繫結訊息對應，請執行下列步驟:  
  
-   從 `CDynamicChain`衍生您的類別。  在訊息對應，請指定 [CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md) 巨集繫結至其他物件預設的訊息對應。  
  
-   取得要繫結至 [CMessageMap](../../atl/reference/cmessagemap-class.md)的每一個類別。  `CMessageMap` 可讓物件將其訊息對應於其他物件。  
  
-   呼叫 `CDynamicChain::SetChainEntry` 識別物件，而且訊息對應您想要繫結。  
  
 例如，假設您的類別定義如下:  
  
 [!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/CPP/cdynamicchain-class_1.h)]  
  
 用戶端會呼叫 `CMyWindow::SetChainEntry`:  
  
 [!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/CPP/cdynamicchain-class_2.cpp)]  
  
 其中 `chainedObj` 是繫結至的物件且使用 `CMessageMap`衍生類別的執行個體。  現在，因此，如果 `myCtl` 收到未 `OnPaint` 或 `OnSetFocus`處理的訊息，視窗程序導向訊息至 `chainedObj` 預設的訊息對應。  
  
 如需繫結訊息的對應的詳細資訊，請參閱 [訊息對應](../../atl/message-maps-atl.md) 本文「ATL 視窗類別上」。  
  
## 需求  
 **Header:** atlwin.h  
  
## 請參閱  
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)