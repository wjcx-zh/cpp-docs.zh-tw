---
title: "SafeIntException::SafeIntException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "SafeIntException"
  - "SafeIntException.SafeIntException"
  - "SafeIntException::SafeIntException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SafeIntException, 建構函式"
ms.assetid: 8e5a0c24-a56b-4c80-9ee8-876604b1e7dc
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 6
---
# SafeIntException::SafeIntException
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

建立 `SafeIntException` 物件。  
  
## 語法  
  
```  
SafeIntException();  
  
SafeIntException(  
   SafeIntError code  
);  
```  
  
#### 參數  
 \[in\] `code`  
 描述錯誤的列舉資料值。  
  
## 備註  
 `code` 的可能值在 Safeint.h 檔案中定義。  為了方便起見，可能的值也會列出此。  
  
-   `SafeIntNoError`  
  
-   `SafeIntArithmeticOverflow`  
  
-   `SafeIntDivideByZero`  
  
## 需求  
 **標頭：** safeint.h  
  
 **命名空間:** msl::utilities  
  
## 請參閱  
 [SafeInt 程式庫](../windows/safeint-library.md)   
 [SafeIntException 類別](../windows/safeintexception-class.md)   
 [SafeInt 類別](../windows/safeint-class.md)