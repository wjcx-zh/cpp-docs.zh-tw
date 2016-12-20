---
title: "ChainInterfaces::CastToUnknown 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::ChainInterfaces::CastToUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CastToUnknown 方法"
ms.assetid: a6a58555-e5b0-4773-aba0-959d9d362c6b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ChainInterfaces::CastToUnknown 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

轉換 `I0` 樣板參數所定義的型別之介面指標的 IUnknown。  
  
## 語法  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## 傳回值  
 IUnknown的指標。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ChainInterfaces 結構](../windows/chaininterfaces-structure.md)