---
title: "implementation_only | Microsoft Docs"
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
  - "implementation_only"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "implementation_only 屬性"
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# implementation_only
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 不產生 .tlh 標頭檔 \(主要標頭檔\)。  
  
## 語法  
  
```  
implementation_only  
```  
  
## 備註  
 這個檔案包含所有用於公開類型程式庫內容的宣告。  實作包裝函式成員函式時，會產生 .tli 標頭檔並包含在編譯中。  
  
 指定這個屬性時，.tli 標頭的內容會在 .tlh 標頭通常使用的相同命名空間中。  此外，不會將成員函式宣告為內嵌。  
  
 `implementation_only` 屬性主要搭配 [no\_implementation](../preprocessor/no-implementation.md) 屬性，用於避開實作先行編譯的標頭 \(PCH\) 檔案。  具有 `no_implementation` 屬性的 `#import` 陳述式是置於用來建立 PCH 的來源範圍中。  產生的 PCH 會供許多原始程式檔使用。  然後具有 `implementation_only` 屬性的 `#import` 陳述式會在 PCH 範圍以外使用。  您只能在其中一個原始程式檔中使用此陳述式一次。  如此會產生所有必要的包裝函式成員函式，而不需要額外重新編譯每個原始程式檔。  
  
> [!NOTE]
>  `#import` 陳述式中的 `implementation_only` 屬性必須與另一個 `#import` 陳述式搭配使用，而該陳述式屬於同一個類型程式庫且具有 `no_implementation` 屬性。  否則，就會產生編譯器錯誤。  這是因為必須要有具 `no_implementation` 屬性的 `#import` 陳述式所產生的包裝函式類別定義，才能編譯 `implementation_only` 屬性所產生的實作。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)