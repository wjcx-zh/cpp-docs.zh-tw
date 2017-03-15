---
title: "ComPtr::operator== 運算子 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::operator=="
dev_langs: 
  - "C++"
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator== 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示兩個 ComPtr 物件是否相等。  
  
## 語法  
  
```cpp  
bool operator==(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator==(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### 參數  
 `a`  
 對 ComPtr 物件的參考。  
  
 `b`  
 對另一個 ComPtr 物件的參考。  
  
## 傳回值  
 如果物件 `a` 相等的物件 `b`，第一個運算子產生 `true` ;否則， `false`。  
  
 如果物件 `a` 與 `nullptr`，等於第二個和第三個運算子產生 `true` ;否則， `false`。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)   
 [ComPtr 類別](../windows/comptr-class.md)