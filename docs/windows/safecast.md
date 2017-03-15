---
title: "SafeCast | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeCast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeCast 函式"
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# SafeCast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

轉換數字的型別轉換為其他型別的。  
  
## 語法  
  
```  
template<typename T, typename U>  
inline bool SafeCast (  
   const T From,  
   U& To  
);  
```  
  
#### 參數  
 \[in\] `From`  
 要轉換的來源數目。  這個必須為型別 T。  
  
 \[out\] `To`  
 對新的數字型別的參考。  這個必須為型別 U。  
  
## 傳回值  
 若沒有錯誤發生則為 `true`；若有錯誤發生則為 `false`。  
  
## 備註  
 這個方法是 [SafeInt 程式庫](../windows/safeint-library.md) 的一部分，為單一轉換運算設計，並且不必建立 [SafeInt 類別](../windows/safeint-class.md) 的執行個體。  
  
> [!NOTE]
>  這個方法只有在當單一運算必須被保護時使用。  如果同時有多個運算，您應該使用 `SafeInt` 類別而不是呼叫個別獨立函式。  
  
 如需此範本類型 T 與 U 的詳細資訊，請參閱 [SafeInt 函式](../windows/safeint-functions.md)。  
  
## 需求  
 **標頭：** safeint.h  
  
 **命名空間：** Microsoft::Utilities  
  
## 請參閱  
 [SafeInt 函式](../windows/safeint-functions.md)   
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)