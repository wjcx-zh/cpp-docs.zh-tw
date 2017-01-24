---
title: "ComPtrRef::operator== 運算子 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::operator=="
dev_langs: 
  - "C++"
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::operator== 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```cpp  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator==(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### 參數  
 `a`  
 ComPtrRef 對物件的參考。  
  
 `b`  
 另一個 ComPtrRef 物件參考或指標給匿名型別 \(`void*`\)。  
  
## 傳回值  
 如果物件 `a` 相等的物件 `b`，第一個運算子產生 `true` ;否則， `false`。  
  
 如果物件 `a` 與 `nullptr`，等於第二個和第三個運算子產生 `true` ;否則， `false`。  
  
 如果物件 `a` 相等的物件 `b`，第四和第五個運算子產生 `true` ;否則， `false`。  
  
## 備註  
 表示兩個 ComPtrRef 物件是否不相等。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef 類別](../windows/comptrref-class.md)