---
title: "使用含有 _MBCS 程式碼的 TCHAR.H 資料類型 | Microsoft Docs"
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
  - ""tchar.h""
  - "TCHAR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "泛用文字資料類型 [C++]"
  - "泛用文字對應 [C++]"
  - "對應泛型文字"
  - "對應 [C++], TCHAR.H"
  - "MBCS [C++], 泛用文字對應"
  - "TCHAR.H 資料類型, 對應"
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 使用含有 _MBCS 程式碼的 TCHAR.H 資料類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資訊清單常數 **\_MBCS** 定義後，給定的泛用文字常式會對應到下列其中一種常式：  
  
-   適用於處理多位元組、字元和字串的 SBCS 常式。  在這個例子裡，期望的字串引數是 **char\*** 型別。  例如，`_tprintf` 對應到 `printf`；`printf` 的字串引數是 **char\*** 型別。  如果使用 **\_TCHAR** 泛用文字資料型別做為您的字串型別，就會符合 `printf` 正式和實際參數型別，因為 **\_TCHAR**\* 對應到 **char\***。  
  
-   MBCS 特定常式。  在這個例子裡，期望的字串引數是 `unsigned` **char\*** 型別。  例如，`_tcsrev` 對應到 `_mbsrev`，期望和傳回 `unsigned` **char\*** 型別的字串。  如果您對您的字串型別使用 **\_TCHAR** 泛用文字資料型別，可能會有型別衝突，因為 **\_TCHAR** 對應到 `char` 型別。  
  
 下列是避免這種型別衝突 \(以及可能造成的 C 編譯器警告或 C\+\+ 編譯器錯誤\) 的三種解決方案：  
  
-   使用預設行為。  Tchar.h 為執行階段程式庫裡的常式提供了泛用文字的常式原型 \(Prototype\)，如下列範例所示。  
  
    ```  
    char * _tcsrev(char *);  
    ```  
  
     在預設的範例裡，`_tcsrev` 的原型經由 Libc.lib 裡的 Thunk 對應到 `_mbsrev`。  這改變了 `_mbsrev` 連入參數和連出傳回值的型別，由 **\_TCHAR \*** \(也就是 `char` **\***\) 到 `unsigned` `char` **\***。  這個方法在您使用 **\_TCHAR** 時會確保型別的對應，但是執行效能會因為函式呼叫的額外負荷而相較慢。  
  
-   藉著在您的程式碼裡結合下列前置處理器陳述式，來使用內嵌函式。  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     這種方法會促使 Tchar.h 所提供的內嵌 Thunk 函式，將泛用文字常式直接對應到適當的 MBCS 常式。  下列程式碼摘錄自 Tchar.h，提供範例來說明這是如何完成。  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     如果您可以使用內嵌，這是最好的解決方法，因為它保證型別符合並且沒有花費額外的時間。  
  
-   藉著在您的程式碼裡結合下列前置處理器陳述式來使用直接對應。  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     這種方法提供快速的替代方案，如果您不想要使用預設行為或不能使用內嵌。  這造成泛用文字常式會直接由巨集對應到 MBCS 版的常式，如同下列來自 Tchar.h 的範例。  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
     當您採用這個方法時，必須小心確保您使用適當的字串引數和字串傳回值的資料型別。  您可以使用型別轉換來確保適當的型別符合，或者您可以使用 **\_TXCHAR** 泛用文字資料型別。  **\_TXCHAR** 在 SBCS 編碼裡對應到 `char` 型別，但是在 MBCS 編碼裡對應到 `unsigned` `char` 型別。  如需泛用文字巨集的詳細資訊，請參閱《執行階段程式庫參考》中的[泛型文字對應](../c-runtime-library/generic-text-mappings.md)。  
  
## 請參閱  
 [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)