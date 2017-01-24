---
title: "SafeInt::SafeInt | Microsoft Docs"
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
  - "SafeInt::SafeInt"
  - "SafeInt"
  - "SafeInt.SafeInt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeInt 類別, 建構函式"
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# SafeInt::SafeInt
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建構 `SafeInt` 物件。  
  
## 語法  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### 參數  
 \[in\] `i`  
 新 `SafeInt` 物件的值。  這必須是型別 T 或 U 的參數，取決於建構函式。  
  
 \[in\] `b`  
 新 `SafeInt` 物件的布林值。  
  
 \[in\] `u`  
 型別為 U 的 `SafeInt`。  新的 `SafeInt` 物件將擁有和 `u` 相同的值，但是型別將會是 T。  
  
 U  
 儲存在 `SafeInt` 內的資料型別。  這可以是布林值、字元或整數型別。  如果是整數型別，它可以是帶正負號或不帶正負號，而且是在 8 和 64 位元組之間。  
  
## 備註  
 如需此範本類型 `T` 和 `E` 的詳細資訊，請參閱 [SafeInt 類別](../windows/safeint-class.md)。  
  
 建構函式的 `i` 或 `u` 輸入參數，必須是布林值、字元或整數型別。  如果是另一個型別的參數，`SafeInt` 類別會呼叫 [static\_assert](../cpp/static-assert.md) 表示無效的輸入參數。  
  
 使用範本型別 `U` 的建構函式會自動轉換輸入參數為 `T` 所指定的型別。  `SafeInt` 類別會轉換資料，而且不會有任何資料遺失。  如果無法將資料轉換為型別 `T` 且沒有資料遺失，則會回報給錯誤處理常式 `E` 。  
  
 如果您從布林參數建立 `SafeInt` ，您需要立即初始化值。  您無法使用程式碼 `SafeInt<bool> sb;` 來建構 `SafeInt`。  這會產生編譯錯誤。  
  
## 需求  
 **標頭：** safeint.h  
  
 **命名空間：** msl::utilities  
  
## 請參閱  
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeInt 類別](../windows/safeint-class.md)   
 [SafeIntException 類別](../windows/safeintexception-class.md)