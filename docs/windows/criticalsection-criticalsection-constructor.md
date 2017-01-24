---
title: "CriticalSection::CriticalSection 建構函式 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSection，建構函式"
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSection::CriticalSection 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化類似 Mutex 物件的同步物件，但是只能給單一處理序的執行緒使用。  
  
## 語法  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### 參數  
 `spincount`  
 關鍵區段物件的微調計數。  預設值為 0。  
  
## 備註  
 如需 crticial 區段和 spincounts 的詳細資訊，請參閱 Windows API documenation 的同步處理部分的 **InitializeCriticalSectionAndSpinCount** 函式。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)