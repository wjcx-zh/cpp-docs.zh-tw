---
title: "SafeMultiply | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeMultiply"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeMultiply 函式"
ms.assetid: 81d988a5-fac7-4930-8c37-c24fa8e2c853
caps.latest.revision: 5
caps.handback.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeMultiply
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同時將兩個數字以防止溢位的方法。  
  
## 語法  
  
```  
template<typename T, typename U>  
inline bool SafeMultiply (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### 參數  
 \[in\] `t`  
 要相乘的第一個數字。  這個必須為型別 T。  
  
 \[in\] `u`  
 要相乘的第二個數字。  這個必須為型別 U。  
  
 \[out\] `result`  
 參數 `SafeMultiply` 儲存結果的位置。  
  
## 傳回值  
 `true` ，如果沒有錯誤發生; `false` ，如果發生錯誤。  
  
## 備註  
 這個方法是 [SafeInt 程式庫](../windows/safeint-library.md) 的一部分為單一乘法運算設計，而不必建立 [SafeInt 類別](../windows/safeint-class.md)的執行個體。  
  
> [!NOTE]
>  這個方法，則必須保護時，才應該使用單一數學運算。  如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需此範本類型 T 與 U 的詳細資訊，請參閱[SafeInt 函式](../windows/safeint-functions.md)。  
  
## 需求  
 **標題:** safeint.h  
  
 **命名空間:** Microsoft::Utilities  
  
## 請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeDivide](../windows/safedivide.md)