---
title: "MakeAllocator::Allocate 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::MakeAllocator::Allocate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Allocate 方法"
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MakeAllocator::Allocate 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
__forceinline void* Allocate();  
```  
  
## 傳回值  
 如果成功，指標指到所配置的記憶體，否則， `nullptr`。  
  
## 備註  
 配置記憶體並將其與目前 MakeAllocator 物件做關聯。  
  
 配置的記憶體大小是目前 MakeAllocator 樣板參數所指定之型別的大小。  
  
 開發人員必須只覆寫配置 Allocate\(\) 方法來實作不同的記憶體配置配置模型。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [MakeAllocator 類別](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)