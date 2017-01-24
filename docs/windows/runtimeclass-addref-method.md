---
title: "RuntimeClass::AddRef 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClass::AddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef 方法"
ms.assetid: 9c705749-680b-4308-bbec-5b601e8e7dbd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass::AddRef 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

遞增目前 RuntimeClass 物件的參考計數。  
  
## 語法  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)