---
title: "Implements::CastToUnknown 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Implements::CastToUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CastToUnknown 方法"
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implements::CastToUnknown 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得基礎 IUnknown 介面的指標。  
  
## 語法  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## 傳回值  
 這個作業一定會成功並傳回 IUnknown 指標。  
  
## 備註  
 內部 Helper 函式。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Implements 結構](../windows/implements-structure.md)