---
title: "Semaphore 類別 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Semaphore 類別"
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Semaphore 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示控制可支援的有限使用者數目的共用資源的同步物件。  
  
## 語法  
  
```  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`SyncLock`|支援同步鎖定的類別的一個同義資料表。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Semaphore::Semaphore 建構函式](../windows/semaphore-semaphore-constructor.md)|初始化新的號誌類別執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[InvokeHelper::Invoke 方法](../windows/invokehelper-invoke-method.md)|呼叫其簽章包含指定數目引數的事件處理常式。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[Semaphore::Lock 方法](../windows/semaphore-lock-method.md)|等候，直到與指定的控制代碼相關的目前物件或號誌物件，處於收到信號狀態或指定的逾時間隔逾時。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[Semaphore::operator\= 運算子](../windows/semaphore-operator-assign-operator.md)|移動指定的控制代碼，從一個號誌物件至目前號誌物件。|  
  
## 繼承階層架構  
 `Semaphore`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)