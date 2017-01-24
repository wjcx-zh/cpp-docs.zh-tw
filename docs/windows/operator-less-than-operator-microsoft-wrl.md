---
title: "operator&lt; 運算子 (Microsoft::WRL) | Microsoft Docs"
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
  - "client/Microsoft::WRL::operator<"
dev_langs: 
  - "C++"
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt; 運算子 (Microsoft::WRL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

判斷物件的位址是否小於另一個。  
  
## 語法  
  
```cpp  
template<class T, class U>  
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();  
template<class T, class U>  
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();  
```  
  
#### 參數  
 `a`  
 左物件。  
  
 `b`  
 右物件。  
  
## 傳回值  
 如果 `a` 位址的值小於 `b` 位址的值，則為 `true`，否則為 `false`。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)