---
title: "SafeDivide | Microsoft Docs"
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
  - "SafeDivide"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeDivide 函式"
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
caps.latest.revision: 5
caps.handback.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeDivide
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

除以兩個數字會防止除以零的方法。  
  
## 語法  
  
```  
template<typename T, typename U>  
inline bool SafeDivide (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### 參數  
 \[in\] `t`  
 除數。  這必須是型別 T。  
  
 \[in\] `u`  
 被除數。  這必須是型別 U。  
  
 \[out\] `result`  
 參數 `SafeDivide` 儲存結果的位置。  
  
## 傳回值  
 `true` ，如果沒有錯誤發生; `false` ，如果發生錯誤。  
  
## 備註  
 這個方法是 [SafeInt 程式庫](../windows/safeint-library.md) 的一部分並提供單一分割作業設計，而不必建立 [SafeInt 類別](../windows/safeint-class.md)的執行個體。  
  
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
 [SafeModulus](../windows/safemodulus.md)   
 [SafeMultiply](../windows/safemultiply.md)