---
title: "必要和選擇性標頭檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.headers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "標頭檔, 執行階段必要項"
  - "Include 檔, 執行階段必要項"
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 必要和選擇性標頭檔
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個執行階段常式的描述包含必要的清單和選擇性包含，或標頭檔 \(.H\)，至該常式。  必要的標頭檔必須包含以得到常式的函式宣告或是另一個常式會在內部呼叫的定義。  選擇性標頭檔通常包括使用預先定義的常數、型別定義或內嵌巨集。  下表列出選擇性標頭檔內容的範例:  
  
|定義|範例|  
|--------|--------|  
|巨集定義|如果程式庫常式實作為巨集，巨集定義可能在原始的常式的標頭檔之外的標頭檔中。  例如， `toupper` 函式巨集定義於標頭檔 CTYPE.H ，而 `_toupper` 在 STDLIB.H宣告。|  
|預定義常數|許多程式庫常式參考在標頭檔中定義的常數。  例如， `_open` 常式使用常數例如 `_O_CREAT`，即於標頭檔 FCNTL.H 定義。|  
|型別定義|某些程式庫常式傳回結構或接受結構做為引數。  例如，資料流 I\/O 常式使用在 STDIO.H 定義的型別 `FILE`的結構。|  
  
 執行階段程式庫標頭檔提供了 ANSI\/ISO C 標準建議模式的函式宣告。  其關聯的函式宣告之後編譯器對任何常式的參考執行型別檢查。  函式宣告對傳回非預設 `int` 型別的常式來說特別重要。  在其宣告未指定其適當的傳回值的常式會由編譯器考慮傳回 `int`，可能會產生未預期的結果。  如需詳細資訊，請參閱 [Type Checking](../c-runtime-library/type-checking-crt.md)。  
  
## 請參閱  
 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)