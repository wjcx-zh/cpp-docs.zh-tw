---
title: "CriticalSection 類別 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSection 類別"
ms.assetid: f2e0a024-71a3-4f6b-99ea-d93a4a608ac4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSection 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示關鍵區段物件。  
  
## 語法  
  
```  
class CriticalSection;  
```  
  
## Members  
  
### 建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CriticalSection::CriticalSection 建構函式](../windows/criticalsection-criticalsection-constructor.md)|初始化類似 Mutex 物件的同步物件，但是只能給單一處理序的執行緒使用。|  
|[CriticalSection::~CriticalSection 解構函式](../windows/criticalsection-tilde-criticalsection-destructor.md)|取消初始化和終結目前 CriticalSection 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CriticalSection::TryLock 方法](../windows/criticalsection-trylock-method.md)|嘗試以不封鎖的方式進入關鍵區段。  如果呼叫成功，則呼叫執行緒會取得關鍵區段的擁有權。|  
|[CriticalSection::Lock 方法](../windows/criticalsection-lock-method.md)|等候指定關鍵區段物件的擁有權。  在呼叫執行緒被授予擁有權時，函式會傳回。|  
|[CriticalSection::IsValid 方法](../windows/criticalsection-isvalid-method.md)|指出目前關鍵區段是否有效。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CriticalSection::cs\_ 資料成員](../windows/criticalsection-cs-data-member.md)|宣告一個關鍵資料成員。|  
  
## 繼承階層架構  
 `CriticalSection`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)