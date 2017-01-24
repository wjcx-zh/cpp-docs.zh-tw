---
title: "Event::operator= 運算子 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 運算子"
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event::operator= 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指派給目前事件執行個體的指定事件的參考。  
  
## 語法  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### 參數  
 `h`  
 為事件執行個體的右值參考。  
  
## 傳回值  
 對目前執行個體的指標。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Event 類別 \(Windows 執行階段 C\+\+ 樣板程式庫\)](../windows/event-class-windows-runtime-cpp-template-library.md)