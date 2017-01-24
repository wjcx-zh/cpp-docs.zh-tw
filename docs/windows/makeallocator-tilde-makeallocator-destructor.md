---
title: "MakeAllocator::~MakeAllocator 解構函式 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~MakeAllocator，解構函式"
ms.assetid: f1299c5f-cc6b-4d4e-85d4-aee1be0e2b0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MakeAllocator::~MakeAllocator 解構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
~MakeAllocator();  
```  
  
## 備註  
 取消初始化 MakeAllocator 類別目前的執行個體。  
  
 此解構函式，如果需要的話，也會刪除基礎的配置的記憶體。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [MakeAllocator 類別](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)