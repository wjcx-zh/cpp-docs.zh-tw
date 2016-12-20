---
title: "RoInitializeWrapper::RoInitializeWrapper 建構函式 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper"
dev_langs: 
  - "C++"
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RoInitializeWrapper::RoInitializeWrapper 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 RoleInitializeWrapper 類別的新執行個體。  
  
## 語法  
  
```cpp  
RoInitializeWrapper(  
   RO_INIT_TYPE flags)  
  
```  
  
#### 參數  
 `flags`  
 其中一 RO\_INIT\_TYPE 列舉型別，指定 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]提供的支援。  
  
## 備註  
 RoInitializeWrapper 類別叫用 Windows::Foundation::Initialize\(*flags*\)。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [HandleT 類別](../windows/handlet-class.md)