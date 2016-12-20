---
title: "RuntimeClass::GetIids 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClass::GetIids"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetIids 方法"
ms.assetid: 826a67d1-ebc4-4940-b5d5-7cd66885e4a1
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClass::GetIids 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得可以包含目前 RuntimeClass 物件實作的介面 ID 的陣列。  
  
## 語法  
  
```  
STDMETHOD(  
   GetIids  
)  
   (_Out_ ULONG *iidCount,   
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### 參數  
 `iidCount`  
 這個作業完成時， `iids`陣列中的項目的總數。  
  
 `iids`  
 這個作業完成時，對陣列的指標介面 ID。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則， E\_OUTOFMEMORY。  
  
## 需求  
 **標題:** implements.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [RuntimeClass 類別](../windows/runtimeclass-class.md)