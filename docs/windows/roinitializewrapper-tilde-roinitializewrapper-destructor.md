---
title: "RoInitializeWrapper::~RoInitializeWrapper 解構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper"
dev_langs: 
  - "C++"
ms.assetid: afef4c1f-ffde-4cd2-8654-8de4182eb5f4
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RoInitializeWrapper::~RoInitializeWrapper 解構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

去初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  
  
## 語法  
  
```cpp  
~RoInitializeWrapper()  
```  
  
## 備註  
 RoInitializeWrapper 類別叫用 Windows::Foundation::Uninitialize \(\)。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HandleT 類別](../windows/handlet-class.md)