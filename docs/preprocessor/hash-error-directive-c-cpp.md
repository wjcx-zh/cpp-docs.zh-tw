---
title: "#error 指示詞 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#error"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#error 指示詞"
  - "error 指示詞 (#error 指示詞)"
  - "前置處理器, 指示詞"
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #error 指示詞 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#error` 指示詞會在編譯時期發出使用者指定的錯誤訊息並結束編輯。  
  
## 語法  
  
```  
#error token-string  
```  
  
## 備註  
 錯誤訊息發出這個指示詞包含 *token\-string* 參數。  `token-string` 參數不是受巨集展開限制。  這個指示詞在前置處理期間，通知開發人員的程式不一致或違規是最有用的條件約束。  下列範例會示範如何處理在前置處理中的錯誤:  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)