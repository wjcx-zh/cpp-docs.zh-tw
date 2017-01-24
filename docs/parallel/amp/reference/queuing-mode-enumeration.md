---
title: "queuing_mode 列舉 | Microsoft Docs"
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
  - "amprt/Concurrency::queuing_mode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "queuing_mode 列舉"
ms.assetid: 8c641054-906d-40b3-bbb4-f62af9356a14
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queuing_mode 列舉
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定快速鍵支援的佇列模式。  
  
## 語法  
  
```  
enum queuing_mode;  
```  
  
## Members  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`queuing_mode_immediate`|佇列模式，此模式會指定任何命令 \(例如，[parallel\_for\_each 函式 \(C\+\+ AMP\)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md)\) 只要傳回給呼叫端，即傳送至對應的加速器裝置。|  
|`queuing_mode_automatic`|佇列模式，此模式會指定將命令排入對應至 [accelerator\_view](../../../parallel/amp/reference/accelerator-view-class.md) 物件的命令佇列。  呼叫 [accelerator\_view::flush](../Topic/accelerator_view::flush%20Method.md) 時，命令會傳送到裝置。|  
  
## 需求  
 **標頭：**amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)