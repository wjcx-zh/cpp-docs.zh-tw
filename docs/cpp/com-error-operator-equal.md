---
title: "_com_error::operator = | Microsoft Docs"
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
  - "_com_error::operator="
  - "_com_error.operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 運算子, 使用特定 Visual C++ 物件"
  - "operator = _com_error 物件"
  - "operator= _com_error 物件"
ms.assetid: b9cc4094-d055-450c-b45a-0a95317488f8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_error::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將現有的 `_com_error` 物件指派給另一個物件。  
  
## 語法  
  
```  
  
      _com_error& operator = (  
   const _com_error& that   
) throw ( );  
```  
  
#### 參數  
 `that`  
 `_com_error` 物件。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_error 類別](../cpp/com-error-class.md)