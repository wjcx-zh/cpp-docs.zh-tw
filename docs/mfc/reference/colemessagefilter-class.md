---
title: "COleMessageFilter Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleMessageFilter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式 [OLE], managing interactions"
  - "COleMessageFilter class"
  - "message filters [C++]"
  - "訊息 [C++], OLE"
  - "OLE [C++], managing concurrency"
  - "OLE 應用程式 [C++], managing interactions"
  - "OLE messages"
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# COleMessageFilter Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

處理 OLE 應用程式的互動所需的並行存取。  
  
## 語法  
  
```  
class COleMessageFilter : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleMessageFilter::COleMessageFilter](../Topic/COleMessageFilter::COleMessageFilter.md)|建構 `COleMessageFilter` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleMessageFilter::BeginBusyState](../Topic/COleMessageFilter::BeginBusyState.md)|在這個忙碌狀態放置應用程式。|  
|[COleMessageFilter::EnableBusyDialog](../Topic/COleMessageFilter::EnableBusyDialog.md)|啟用和停用時出現的對話方塊會呼叫應用程式忙碌中。|  
|[COleMessageFilter::EnableNotRespondingDialog](../Topic/COleMessageFilter::EnableNotRespondingDialog.md)|啟用和停用時出現的對話方塊會呼叫應用程式沒有回應。|  
|[COleMessageFilter::EndBusyState](../Topic/COleMessageFilter::EndBusyState.md)|結束應用程式忙碌狀態。|  
|[COleMessageFilter::OnMessagePending](../Topic/COleMessageFilter::OnMessagePending.md)|呼叫由架構處理訊息，當一個 OLE 呼叫正在進行中時。|  
|[COleMessageFilter::Register](../Topic/COleMessageFilter::Register.md)|註冊具有 OLE 系統 DLL 的訊息篩選條件。|  
|[COleMessageFilter::Revoke](../Topic/COleMessageFilter::Revoke.md)|移除與這個 OLE 系統 DLL 的訊息篩選條件的註冊。|  
|[COleMessageFilter::SetBusyReply](../Topic/COleMessageFilter::SetBusyReply.md)|判斷為 OLE 呼叫忙碌應用程式的回覆。|  
|[COleMessageFilter::SetMessagePendingDelay](../Topic/COleMessageFilter::SetMessagePendingDelay.md)|判斷應用程式等候至 OLE 呼叫的回應。|  
|[COleMessageFilter::SetRetryReply](../Topic/COleMessageFilter::SetRetryReply.md)|判斷重新命名忙碌應用程式的呼叫應用程式的回覆。|  
  
## 備註  
 `COleMessageFilter` 類別適用於視覺化編輯伺服器和容器應用程式，以及 OLE Automation 應用程式。  對於名為的伺服器應用程式，這個類別可用來讓應用程式「忙碌」，以便從其他容器應用程式是在呼叫之後取消或重試。  當呼叫應用程式忙碌中時，這個類別也可用於判斷集合中呼叫的應用程式要採取的動作。  
  
 常見的用法是針對伺服器應用程式可以呼叫 [BeginBusyState](../Topic/COleMessageFilter::BeginBusyState.md) 和 [EndBusyState](../Topic/COleMessageFilter::EndBusyState.md) ，當有危險為了要終結的檔案或其他 OLE 可存取物件。  在使用者介面更新時，這些呼叫在 [CWinApp::OnIdle](../Topic/CWinApp::OnIdle.md) 進行。  
  
 根據預設， `COleMessageFilter` 物件，以在應用程式初始化時，配置。  它可以擷取與 [AfxOleGetMessageFilter](../Topic/AfxOleGetMessageFilter.md)。  
  
 這是進階的類別;您很少需要直接與一起使用。  
  
 如需詳細資訊，請參閱本文 [伺服器:實作伺服器](../../mfc/servers-implementing-a-server.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)