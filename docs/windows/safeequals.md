---
title: "SafeEquals | Microsoft Docs"
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
  - "SafeEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeEquals 函式"
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
caps.latest.revision: 6
caps.handback.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeEquals
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

比較兩個數字，判斷它們是否相等。  
  
## 語法  
  
```  
template<typename T, typename U>  
inline bool SafeEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### 參數  
 \[in\] `t`  
 要比較的第一個數字。  這個必須為型別 T。  
  
 \[in\] `u`  
 要比較的第二個數字。  這個必須為型別 U。  
  
## 傳回值  
 如果 `t` 和 `u` 相等則為 `true`，否則為 `false`。  
  
## 備註  
 因為 `SafeEquals` 可讓您比較兩種不同型別的數字，此方法則會引發 `==` 。  
  
 這個方法是 [SafeInt 程式庫](../windows/safeint-library.md) 的一部分，為單一比較運算設計，並且不必建立 [SafeInt 類別](../windows/safeint-class.md) 的執行個體。  
  
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
 [SafeNotEquals](../windows/safenotequals.md)