---
title: "HandleT::HandleT 建構函式 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HandleT, 建構函式"
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HandleT::HandleT 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 HandleT 類別的新執行個體。  
  
## 語法  
  
```  
explicit HandleT(  
   typename HandleTraits::Type h =   
      HandleTraits::GetInvalidValue()  
);  
  
HandleT(  
   _Inout_ HandleT&& h  
);  
```  
  
#### 參數  
 `h`  
 控制代碼。  
  
## 備註  
 第一個建構函式初始化不是有效的控制代碼的 HandleT 物件為物件。  第二個建構函式會從參數 `h`建立一個新 HandleT 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HandleT 類別](../windows/handlet-class.md)