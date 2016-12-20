---
title: "搭配使用 TCHAR.H 資料類型與 _MBCS | Microsoft Docs"
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
  - "_mbcs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_MBCS 資料類型"
  - "MBCS 資料類型"
  - "TCHAR.H 資料類型"
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 搭配使用 TCHAR.H 資料類型與 _MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 泛用文字常式對應指示資料表 \(請參閱 [泛用文字對應。](../c-runtime-library/generic-text-mappings.md)\)，當資訊清單常數 `_MBCS` 被定義，特定泛用文字常式對應到下列其中一個常式:  
  
-   適用於處理多位元組、字元和字串的 SBCS 常式。  在這個例子裡，期望的字串引數是 `char*` 型別。  例如，`_tprintf` 對應到 `printf`；`printf` 的字串引數是 `char*` 型別。  如果使用 `__TCHAR` 泛用文字資料型別做為您的字串型別，就會符合 `printf` 正式和實際參數型別，因為 `_TCHAR*`對應到`char*`。  
  
-   MBCS 特定常式。  在這個例子裡，期望的字串引數是 `unsigned char*`型別。  例如，`_tcsrev`  對應到 `_mbsrev`，期望和傳回 `unsigned char*` 型別的字串。  如果您對您的字串型別使用 `_TCHAR` 泛用文字資料型別，可能會有型別衝突，因為  `_TCHAR` 對應到 `char`型別。  
  
 下列是避免這種型別衝突 \(以及可能造成的 C 編譯器警告或 C\+\+ 編譯器錯誤\) 的三種解決方案：  
  
-   使用預設行為。  TCHAR.H 為執行階段程式庫裡的常式提供了泛用文字的常式原型 \(Prototype\)，如下列範例所示。  
  
    ```  
    char *_tcsrev(char *);  
    ```  
  
     在預設的範例裡，`_tcsrev` 的原型經由 LIBC.LIB 裡的 Thunk 對應到 `_mbsrev`。  這改變了 `_mbsrev` 連入參數和連出傳回值的型別，由 `_TCHAR *`\(也就是 `char *``unsigned char *`\)。  您在使用`_TCHAR` 這個方法時，會確保型別的對應，但是執行效能會因為函式呼叫的額外負荷而相較慢。  
  
-   藉著在您的程式碼裡結合下列前置處理器陳述式，來使用內嵌函式。  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     這種方法會促使 TCHAR.H所提供的內嵌 Thunk 函式，將泛用文字常式直接對應到適當的 MBCS 常式。  下列程式碼摘錄自 TCHAR.H，提供範例來說明這是如何完成。  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     如果您可以使用內嵌，這是最好的解決方法，因為它保證型別符合並且沒有花費額外的時間。  
  
-   藉著在您的程式碼裡結合下列前置處理器陳述式來使用「直接對應」。  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     這種方法提供快速的替代方案，如果您不想要使用預設行為或不能使用內嵌。  這造成泛用文字常式會直接由巨集對應到 MBCS 版的常式，如同下列來自 TCHAR.H的範例。  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
 當您採用這個方法時，必須小心確保您使用適當的字串引數和字串傳回值的資料型別。  您可以使用型別轉換來確保適當的型別符合，或者您可以使用 `_TXCHAR` 泛用文字資料型別。  `_TXCHAR` 在 SBCS 編碼裡對應到 `char` 型別，但是在 MBCS 編碼裡對應到 `unsigned char`  型別。  如需泛用文字巨集的詳細資訊，請參閱 [泛用文字對應。](../c-runtime-library/generic-text-mappings.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)