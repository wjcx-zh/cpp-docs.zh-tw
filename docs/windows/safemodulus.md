---
title: "SafeModulus | Microsoft Docs"
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
  - "SafeModulus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeModulus 函式"
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
caps.latest.revision: 6
caps.handback.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeModulus
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

執行兩個數字的模數運算。  
  
## 語法  
  
```  
template<typename T, typename U>  
inline bool SafeModulus (  
   const T t,  
   const U u,  
   T& result  
) throw ();  
```  
  
#### 參數  
 \[in\] `t`  
 除數。  這個必須為型別 T。  
  
 \[in\] `u`  
 被除數。  這個必須為型別 U。  
  
 \[out\] `result`  
 `SafeModulus` 儲存結果的參數。  
  
## 傳回值  
 若沒有錯誤發生則為 `true`；若有錯誤發生則為 `false`。  
  
## 備註  
 這個方法是 [SafeInt 程式庫](../windows/safeint-library.md) 的一部分，為單一模數運算設計，並且不必建立 [SafeInt 類別](../windows/safeint-class.md) 的執行個體。  
  
> [!NOTE]
>  這個方法只有在當單一數學運算必須被保護時使用。  如果同時有多個運算，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需此範本類型 T 與 U 的詳細資訊，請參閱 [SafeInt 函式](../windows/safeint-functions.md)。  
  
## 需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## 請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeDivide](../windows/safedivide.md)