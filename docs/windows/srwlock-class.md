---
title: "SRWLock 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLock 類別"
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# SRWLock 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示一個輕型讀取器\/寫入器鎖定。  
  
## 語法  
  
```  
class SRWLock;  
```  
  
## 備註  
 一個微小的讀取器\/寫入器鎖定是用來同步處理跨執行緒存取物件或資源。  如需詳細資訊，請參閱 MSDN Library 中的 [同步處理函式](http://msdn.microsoft.com/zh-tw/9b6359c2-0113-49b6-83d0-316ad95aba1b) 。  
  
## Members  
  
### 公用 Typedefs  
  
|||  
|-|-|  
|**SyncLockExclusive**|以獨佔模式取得的 SRWLock 物件的同義字。|  
|**SyncLockShared**|在共用模式中取得的 SRWLock 物件的同義字。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[SRWLock::SRWLock 建構函式](../windows/srwlock-srwlock-constructor.md)|初始化新的 SRWLock 類別執行個體。|  
|[SRWLock::~SRWLock 解構函式](../windows/srwlock-tilde-srwlock-destructor.md)|取消初始化 SRWLock 類別的執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[SRWLock::LockExclusive 方法](../windows/srwlock-lockexclusive-method.md)|以獨佔模式取得一 SRWLock 物件。|  
|[SRWLock::LockShared 方法](../windows/srwlock-lockshared-method.md)|在共用模式中取得一個 SRWLock 物件。|  
|[SRWLock::TryLockExclusive 方法](../windows/srwlock-trylockexclusive-method.md)|嘗試取得以獨佔模式目前或指定之 SRWLock 物件的 SRWLock 物件。|  
|[SRWLock::TryLockShared 方法](../windows/srwlock-trylockshared-method.md)|嘗試為目前或指定之 SRWLock 物件在共用模式中取得一個 SRWLock 物件。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[SRWLock::SRWLock\_ 資料成員](../windows/srwlock-srwlock-data-member.md)|包含目前 SRWLock 物件的基礎的變數。|  
  
## 繼承階層架構  
 `SRWLock`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)