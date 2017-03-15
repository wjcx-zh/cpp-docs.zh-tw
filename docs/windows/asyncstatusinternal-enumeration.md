---
title: "AsyncStatusInternal 列舉 | Microsoft Docs"
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
  - "async/Microsoft::WRL::Details::AsyncStatusInternal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncStatusInternal 列舉"
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncStatusInternal 列舉
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
enum AsyncStatusInternal;  
```  
  
## 備註  
 指定內部列舉非同步作業的狀態和 **Windows::Foundation::AsyncStatus** 列舉型別之間的對應。  
  
## Members  
 `_Created`  
 為::Windows::Foundation::AsyncStatus::Created 的對等用法  
  
 `_Started`  
 為::Windows::Foundation::AsyncStatus::Started 的對等用法  
  
 `_Completed`  
 為::Windows::Foundation::AsyncStatus::Completed 的對等用法  
  
 `_Cancelled`  
 為::Windows::Foundation::AsyncStatus::Cancelled 的對等用法  
  
 `_Error`  
 為::Windows::Foundation::AsyncStatus::Error 的對等用法  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)