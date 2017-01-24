---
title: "Event 類別 (Windows 執行階段 C++ 樣板程式庫) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event"
dev_langs: 
  - "C++"
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event 類別 (Windows 執行階段 C++ 樣板程式庫)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示事件。  
  
## 語法  
  
```  
class Event : public HandleT<HandleTraits::EventTraits>;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|說明|  
|--------|--------|  
|[Event::Event 建構函式 \(Windows 執行階段 C\+\+ 樣板程式庫\)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|初始化 Event 類別的新執行個體。|  
  
### 公用運算子  
  
|名稱|說明|  
|--------|--------|  
|[Event::operator\= 運算子](../windows/event-operator-assign-operator.md)|將指定的 Event 參考指派給目前的 Event 執行個體。|  
  
## 繼承階層  
 `HandleT`  
  
 `Event`  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)