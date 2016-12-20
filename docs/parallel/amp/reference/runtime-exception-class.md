---
title: "runtime_exception 類別 | Microsoft Docs"
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
  - "amp/Concurrency::direct3d_abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "runtime_exception 類別"
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# runtime_exception 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

C\+\+ Accelerated Massive Parallelism \(AMP\) 函式庫中例外的基底型別。  
  
## 語法  
  
```  
class runtime_exception : public std::exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[runtime\_exception::runtime\_exception 建構函式](../Topic/runtime_exception::runtime_exception%20Constructor.md)|初始化 `runtime_exception` 類別的新執行個體。|  
|[runtime\_exception::~runtime\_exception 解構函式](../Topic/runtime_exception::~runtime_exception%20Destructor.md)|終結 `runtime_exception` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[runtime\_exception::get\_error\_code 方法](../Topic/runtime_exception::get_error_code%20Method.md)|傳回造成例外狀況的錯誤碼。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[runtime\_exception::operator\= 運算子](../Topic/runtime_exception::operator=%20Operator.md)|將此 `runtime_exception` 物件的內容寫入這個物件。|  
  
## 繼承階層架構  
 `exception`  
  
 `runtime_exception`  
  
## 需求  
 **標頭:**  amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)