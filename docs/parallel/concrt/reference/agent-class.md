---
title: "agent 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::agent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "agent 類別"
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# agent 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

分類適用於做為所有獨立代理程式的基底類別。  它用來隱藏 \[從其他代理程式的狀態，以及互動使用訊息傳遞。  
  
## 語法  
  
```  
class agent;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[agent::agent 建構函式](../Topic/agent::agent%20Constructor.md)|多載。  建構代理程式。|  
|[agent::~agent 解構函式](../Topic/agent::~agent%20Destructor.md)|終結代理程式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[agent::cancel 方法](../Topic/agent::cancel%20Method.md)|將代理程式從 `agent_created` 或 `agent_runnable` 狀態移至 `agent_canceled` 狀態。|  
|[agent::start 方法](../Topic/agent::start%20Method.md)|將代理程式從 `agent_created` 狀態移至 `agent_runnable` 狀態，並且排成它進行執行。|  
|[agent::status 方法](../Topic/agent::status%20Method.md)|代理程式的同步狀態資訊來源。|  
|[agent::status\_port 方法](../Topic/agent::status_port%20Method.md)|代理程式的非同步狀態資訊來源。|  
|[agent::wait 方法](../Topic/agent::wait%20Method.md)|等候代理程式完成其工作。|  
|[agent::wait\_for\_all 方法](../Topic/agent::wait_for_all%20Method.md)|等候所有指定的代理程式完成其工作。|  
|[agent::wait\_for\_one 方法](../Topic/agent::wait_for_one%20Method.md)|等候任何一個指定的代理程式完成其工作。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[agent::done 方法](../Topic/agent::done%20Method.md)|將代理程式移至 `agent_done` 狀態，表示該代理程式已完成。|  
|[agent::run 方法](../Topic/agent::run%20Method.md)|代表代理程式的主要工作。  `run` 應在衍生類別中覆寫，且指定代理程式在它啟動後應該執行的動作。|  
  
## 備註  
 如需詳細資訊，請參閱 [非同步代理程式](../../../parallel/concrt/asynchronous-agents.md)。  
  
## 繼承階層架構  
 `agent`  
  
## 需求  
 **標頭：** agents.h  
  
 **Namespace:** 並行存取  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)