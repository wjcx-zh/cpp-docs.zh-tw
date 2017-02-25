---
title: "accelerator_view_removed 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::accelerator_view_removed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "amprt/Concurrency::accelerator_view_removed 類別"
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# accelerator_view_removed 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

當一個基礎 DirectX 呼叫失敗因為 Windows 逾時偵測和復原機制所擲回的例外狀況。  
  
## 語法  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[accelerator\_view\_removed::accelerator\_view\_removed 建構函式](../Topic/accelerator_view_removed::accelerator_view_removed%20Constructor.md)|初始化 `accelerator_view_removed` 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[accelerator\_view\_removed::get\_view\_removed\_reason 方法](../Topic/accelerator_view_removed::get_view_removed_reason%20Method.md)|傳回指示 `accelerator_view` 物件移除的原因的一個 HRESULT 錯誤碼。|  
  
## 繼承階層架構  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## 需求  
 **標頭:**  amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)