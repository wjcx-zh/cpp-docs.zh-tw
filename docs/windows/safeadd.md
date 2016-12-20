---
title: "SafeAdd | Microsoft Docs"
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
  - "SafeAdd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeAdd 函式"
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeAdd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以防止溢位的方法加入兩個數字。  
  
## 語法  
  
```  
template<typename T, typename U>  
inline bool SafeAdd (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### 參數  
 \[in\] `t`  
 要加入的第一個數字。  這個必須為型別 T。  
  
 \[in\] `u`  
 要加入的第二個數字。  這個必須為型別 U。  
  
 \[out\] `result`  
 `SafeAdd` 儲存結果的參數。  
  
## 傳回值  
 若沒有錯誤發生則為 `true`；若有錯誤發生則為 `false`。  
  
## 備註  
 這個方法是 [SafeInt 程式庫](../windows/safeint-library.md) 的一部分，為單一相加運算設計，並且不必建立 [SafeInt 類別](../windows/safeint-class.md) 的執行個體。  
  
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
 [SafeSubtract](../windows/safesubtract.md)