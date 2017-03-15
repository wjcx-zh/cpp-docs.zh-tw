---
title: "ComPtr::Attach 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::Attach 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使這 ComPtr 與目前範本型別參數指定的介面型別關連。  
  
## 語法  
  
```  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
#### 參數  
 `other`  
 介面型別。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ComPtr 類別](../windows/comptr-class.md)