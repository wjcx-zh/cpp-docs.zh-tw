---
title: "SyncLockT 類別 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockT 類別"
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockT 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
#### 參數  
 `SyncTraits`  
 可以取得資源的擁有權的型別。  
  
## 備註  
 表示可以取得資源的獨佔或共用擁有權的型別。  
  
 SyncLockT 類別被使用，例如，幫助實作 [SRWLock](../windows/srwlock-class.md) 類別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[SyncLockT::SyncLockT 建構函式](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 類別的新執行個體。|  
|[SyncLockT::~SyncLockT 解構函式](../windows/synclockt-tilde-synclockt-destructor.md)|取消初始化 SyncLockT 類別的執行個體。|  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[SyncLockT::SyncLockT 建構函式](../windows/synclockt-synclockt-constructor.md)|初始化 SyncLockT 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[SyncLockT::IsLocked 方法](../windows/synclockt-islocked-method.md)|指示目前的SyncLockT物件是否擁有資源;也就是說 SyncLockT 物件已*被鎖定*。|  
|[SyncLockT::Unlock 方法](../windows/synclockt-unlock-method.md)|資源的釋放控制項是由目前物件 SyncLockT 持有，如果有的話。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[SyncLockT::sync\_ 資料成員](../windows/synclockt-sync-data-member.md)|保留以 SyncLockT 類別為代表的基礎資源。|  
  
## 繼承階層架構  
 `SyncLockT`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::Details 命名空間](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock 類別](../windows/srwlock-class.md)