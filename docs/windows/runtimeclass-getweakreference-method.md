---
title: "RuntimeClass::GetWeakReference 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClass::GetWeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetWeakReference 方法"
ms.assetid: 26656ace-7f20-4364-87c9-4a75dd30912e
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass::GetWeakReference 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得指向目前 RuntimeClass 物件的弱式參考物件的指標。  
  
## 語法  
  
```  
STDMETHOD(  
   GetWeakReference  
)(_Deref_out_ IWeakReference **weakReference);  
```  
  
#### 參數  
 `weakReference`  
 這個作業完成時，為弱式參考物件的指標。  
  
## 傳回值  
 永遠為 S\_OK。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)