---
title: "lock 類別 | Microsoft Docs"
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
  - "msclr::lock"
  - "msclr.lock"
  - "lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock 類別"
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# lock 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個類別會自動採用同步存取鎖定為從多個執行緒的物件。在建構它取得鎖定，而且，排程器會釋放鎖定。  
  
## 語法  
  
```  
ref class lock;  
```  
  
## 備註  
 `lock` 為 CLR 物件只可使用，而且只能在 CLR 程式碼。  
  
 在內部，鎖定層級使用 <xref:System.Threading.Monitor> 同步存取。  請參閱這個主題有關同步處理的詳細資訊。  
  
## 需求  
 **標頭檔** \<msclr\\lock.h\>  
  
 **命名空間** msclr  
  
## 請參閱  
 [lock](../dotnet/lock.md)   
 [lock 成員](../dotnet/lock-members.md)