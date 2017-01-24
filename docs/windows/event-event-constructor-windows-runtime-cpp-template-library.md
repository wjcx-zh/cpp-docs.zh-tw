---
title: "Event::Event 建構函式 (Windows 執行階段 C++ 樣板程式庫) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Event::Event"
dev_langs: 
  - "C++"
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Event::Event 建構函式 (Windows 執行階段 C++ 樣板程式庫)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 Event 類別的新執行個體。  
  
## 語法  
  
```  
explicit Event(  
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);  
WRL_NOTHROW Event(  
   _Inout_ Event&& h  
);  
```  
  
#### 參數  
 `h`  
 事件的控制代碼。  根據預設，`h` 初始化為 `nullptr`。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [Event 類別 \(Windows 執行階段 C\+\+ 樣板程式庫\)](../windows/event-class-windows-runtime-cpp-template-library.md)