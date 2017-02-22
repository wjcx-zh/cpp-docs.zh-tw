---
title: "FactoryCache::cookie 資料成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::FactoryCache::cookie"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cookie 資料成員"
ms.assetid: b1bc79af-a896-4e3b-8afa-64733022eddf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# FactoryCache::cookie 資料成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基礎結構，而且不是針對直接從程式碼中使用而設計。  
  
## 語法  
  
```  
union {   
   WINRT_REGISTRATION_COOKIE winrt;  
   DWORD com;   
} cookie;  
```  
  
## 備註  
 包含一個可識別已註冊的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 或 COM 類別物件的值，並稍後用來解除註冊物件。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [FactoryCache 結構](../windows/factorycache-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)