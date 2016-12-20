---
title: "unsupported_feature 類別 | Microsoft Docs"
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
  - "amprt/Concurrency::unsupported_feature"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unsupported_feature 類別"
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unsupported_feature 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

使用不支援的功能時，所擲回的例外狀況。  
  
## 語法  
  
```  
class unsupported_feature : public runtime_exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[unsupported\_feature::unsupported\_feature 建構函式](../Topic/unsupported_feature::unsupported_feature%20Constructor.md)|建構 `unsupported_feature` 例外狀況的新執行個體。|  
  
## 繼承階層架構  
 `exception`  
  
 `runtime_exception`  
  
 `unsupported_feature`  
  
## 需求  
 **標頭：**amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)