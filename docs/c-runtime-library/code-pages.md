---
title: "字碼頁 | Microsoft Docs"
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
  - "c.international"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ANSI [C++], 字碼頁"
  - "字元集 [C++], 字碼頁"
  - "字碼頁 [C++], 類型"
  - "地區設定字碼頁 [C++]"
  - "當地語系化 [C++], 字碼頁"
  - "多位元組字碼頁 [C++]"
  - "系統預設字碼頁"
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 字碼頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`code page` 是字元集，可能包括數字、標點符號和其他圖像。  不同語言和地區可能使用不同的字碼頁。  例如，ANSI 字碼頁 1252 是用於英語和大多數歐洲語言，而 OEM 字碼頁 932 是用於日語漢字。  
  
 字碼頁在資料表中可以表示為字元對應到單一位元組值或多位元組值。  許多字碼頁共用 ASCII 字元集字元的範圍為 0x00 – 0x7F。  
  
 Microsoft Run\-Time 程式庫使用字碼頁的下列型別:  
  
-   系統預設 ANSI 字碼頁  根據預設，在開始時 run\-time 系統會自動將多位元組字碼頁設為從作業系統取得的系統預設ANSI字碼頁。  呼叫:  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     也會將地區設定為系統預設 ANSI 字碼頁。  
  
-   地區設定字碼頁。  階段常式數量的行為取決於目前的地區設定，包括地區設定字碼頁。\(如需詳細資訊，請參閱 [地區設定相關常式](../c-runtime-library/locale.md)\)。根據預設，所有在 Microsoft 執行階段程式庫中的地區相關設定使用對應至「C」地區設定的字碼頁。  在執行階段可以呼叫 [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)變更或查詢的地區設定字碼頁。  
  
-   多位元組字碼頁  大部分多位元組字元常式在這個執行階段程式庫中的行為取決於目前多位元組字碼頁。  根據預設，這些常式使用系統預設 ANSI 字碼頁。  在執行階段可以分別使用[\_getmbcp](../c-runtime-library/reference/getmbcp.md) 和 [\_setmbcp](../c-runtime-library/reference/setmbcp.md)查詢和變更多位元組字碼頁。  
  
-   「C」地區設定是由 ANSI 定義以對應 C 程式傳統上執行的地區設定。  「C」地區設定 \(「C」字碼頁\) 字碼頁對應 ASCII 字元集。  例如， 「C」地區設定， 對於 0x61 – 0x7A`islower` 只傳回 true 的值 。  在另一個地區設定， 對於這些以及其他由該地區設定所定義的值`islower` 可能會傳回 true。  
  
## 請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)