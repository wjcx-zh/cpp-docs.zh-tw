---
title: "AsyncBase::OnClose 方法 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::OnClose"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OnClose 方法"
ms.assetid: 96766450-c262-4611-8534-7d190b799142
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::OnClose 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在衍生類別中覆寫時，關閉非同步作業。  
  
## 語法  
  
```  
virtual void OnClose(  
   void  
) = 0;  
```  
  
## 需求  
 **標題:** async.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [AsyncBase 類別](../windows/asyncbase-class.md)   
 [AsyncBase::Close 方法](../windows/asyncbase-close-method.md)