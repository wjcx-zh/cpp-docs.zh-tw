---
title: "SafeLessThanEquals | Microsoft Docs"
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
  - "SafeLessThanEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeLessThanEquals 函式"
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
caps.latest.revision: 6
caps.handback.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeLessThanEquals
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

比較兩個數字。  
  
## 語法  
  
```  
template <typename T, typename U>  
inline bool SafeLessThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### 參數  
 \[in\] `t`  
 要比較的第一個數字。  這必須是型別 T。  
  
 \[in\] `u`  
 要比較的第二個數字。  這必須是型別 U。  
  
## 傳回值  
 `true` ，如果 `t` 小於或等於 `u`;否則為 `false`。  
  
## 備註  
 `SafeLessThanEquals` 可以讓您比較數值的兩種不同類型的擴充泛型比較運算子。  
  
 這個方法是 [SafeInt 程式庫](../windows/safeint-library.md) 的一部分為單一比較作業設計，而不必建立 [SafeInt 類別](../windows/safeint-class.md)的執行個體。  
  
> [!NOTE]
>  這個方法，則必須保護時，才應該使用單一數學運算。  如果有多個作業，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需範本型別 T 和 U 的詳細資訊，請參閱 [SafeInt 函式](../windows/safeint-functions.md)。  
  
## 需求  
 **標題:** safeint.h  
  
 **命名空間:** Microsoft::Utilities  
  
## 請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThan](../windows/safelessthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)