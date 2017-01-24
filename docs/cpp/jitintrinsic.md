---
title: "jitintrinsic | Microsoft Docs"
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
  - "jitintrinsic"
  - "jitintrinsic_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], jitintrinsic"
  - "jitintrinsic __declspec 修飾詞"
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# jitintrinsic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將函式標記為 64 位元 Common Language Runtime 的必要項。  這種方式會在 Microsoft 所提供程式庫中的某些函式上使用。  
  
## 語法  
  
```  
__declspec(jitintrinsic)  
```  
  
## 備註  
 `jitintrinsic` 會將 MODOPT \(<xref:System.Runtime.CompilerServices.IsJitIntrinsic>\) 加入至函式簽章。  
  
 由於可能發生無法預期的結果，因此不建議使用者使用這個 `__declspec` 修飾詞。  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)