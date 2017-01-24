---
title: "MakeAllocator 類別 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::MakeAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MakeAllocator 類別"
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MakeAllocator 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
  
template<  
   typename T,  
   bool hasWeakReferenceSupport =   
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,   
   T)> , T)> class MakeAllocator;  
  
template<  
   typename T  
>  
class MakeAllocator<T, false>;  
  
template<  
   typename T  
>  
class MakeAllocator<T, true>;  
```  
  
#### 參數  
 `T`  
 型別名稱。  
  
 `hasWeakReferenceSupport`  
 `true` 以配置支援弱式參考的物件記憶體; `false` 以配置不支援弱式參考的物件記憶體。  
  
## 備註  
 配置可啟動類別的記憶體，使用或不使用弱式參考支援。  
  
 覆寫 MakeAllocator 類別來實作一個使用者定義的記憶體配置配置模型。  
  
 MakeAllocator 通常用於防止記憶體遺漏 \(Memory Leak\)，一旦在建構期間物件被擲回。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[MakeAllocator::MakeAllocator 建構函式](../windows/makeallocator-makeallocator-constructor.md)|初始化 MakeAllocator 類別的新執行個體。|  
|[MakeAllocator::~MakeAllocator 解構函式](../windows/makeallocator-tilde-makeallocator-destructor.md)|取消初始化 MakeAllocator 類別目前的執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[MakeAllocator::Allocate 方法](../windows/makeallocator-allocate-method.md)|配置記憶體並將其與目前 MakeAllocator 物件做關聯。|  
|[MakeAllocator::Detach 方法](../windows/makeallocator-detach-method.md)|從目前的 MakeAllocator 物件中分隔 [Allocate](../windows/makeallocator-allocate-method.md) 方法所配置的記憶體。|  
  
## 繼承階層架構  
 `MakeAllocator`  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)