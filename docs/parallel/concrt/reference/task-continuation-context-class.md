---
title: "task_continuation_context 類別 | Microsoft Docs"
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
  - "ppltasks/concurrency::task_continuation_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_continuation_context 類別"
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 15
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_continuation_context 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`task_continuation_context` 類別可讓您指定要在何處執行接續。  只有從 Windows 市集應用程式使用這個類別才有用。  對於非 Windows 市集應用程式，接續的執行內容取決於執行階段工作，而且不可設定。  
  
## 語法  
  
```  
class task_continuation_context : public details::_ContextCallback;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[task\_continuation\_context::use\_arbitrary 方法](../Topic/task_continuation_context::use_arbitrary%20Method.md)|建立能夠讓執行階段選擇接續執行內容的工作接續內容。|  
|[task\_continuation\_context::use\_current 方法](../Topic/task_continuation_context::use_current%20Method.md)|傳回表示目前執行內容的工作接續內容物件。|  
|[task\_continuation\_context::use\_default 方法](../Topic/task_continuation_context::use_default%20Method.md)|建立預設工作接續內容。|  
  
## 繼承階層架構  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## 需求  
 **標頭：**ppltasks.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task Class](http://msdn.microsoft.com/zh-tw/5389e8a5-5038-40b6-844a-55e9b58ad35f)