---
title: "Mutex 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Mutex 類別"
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Mutex 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示完全控制共用資源的同步物件。  
  
## 語法  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|**SyncLock**|支援同步鎖定的類別的一個同義資料表。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Mutex::Mutex 建構函式](../windows/mutex-mutex-constructor.md)|初始化 Mutex 類別的新執行個體。|  
  
### 公用成員  
  
|名稱|描述|  
|--------|--------|  
|[Mutex::Lock 方法](../windows/mutex-lock-method.md)|等候，直到目前物件、Mutex 物件與指定控制代碼、釋放 Mutex 或指定的逾時間隔耗用的時間。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[Mutex::operator\= 運算子](../windows/mutex-operator-assign-operator.md)|指派 \(移動\) 指定的 Mutex 物件至目前 Mutex 物件。|  
  
## 繼承階層架構  
 `Mutex`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)