---
title: "RuntimeClass::Release 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClass::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release 方法"
ms.assetid: 0bd6f9e2-ad90-4de6-adef-a6286f458cb6
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass::Release 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在目前的 RuntimeClass 物件執行 COM 版本作業。  
  
## 語法  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，表示錯誤的 HRESULT。  
  
## 備註  
 如果參考計數變成零， RuntimeClass 物件會被刪除。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)