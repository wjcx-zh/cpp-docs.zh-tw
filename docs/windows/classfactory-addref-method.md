---
title: "ClassFactory::AddRef 方法 | Microsoft Docs"
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
  - "module/Microsoft::WRL::ClassFactory::AddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef 方法"
ms.assetid: 5b091785-dea4-42b6-a502-0db5fc7a5a2e
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ClassFactory::AddRef 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遞增目前 ClassFactory 物件的參考計數。  
  
## 語法  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## 傳回值  
 如果成功，則為 S\_OK，否則即為描述失敗的 HRESULT。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [ClassFactory 類別](../windows/classfactory-class.md)