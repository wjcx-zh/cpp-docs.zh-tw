---
title: "ComPtr::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: aa6a46f7-f56b-4fd5-add0-7cea55f7abda
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::Reset
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

釋放與這個 ComPtr 相關聯的介面指標的所有參考。  
  
## 語法  
  
```  
unsigned long Reset();  
```  
  
## 傳回值  
 釋放的參考數目 \(若有的話\)。  
  
## 需求  
 **標頭：**client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)