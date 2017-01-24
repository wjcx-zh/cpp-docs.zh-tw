---
title: "#if、#elif、#else 和 #endif 指示詞 (C/C++) | Microsoft Docs"
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
  - "#else"
  - "#endif"
  - "#if"
  - "#elif"
  - "Defined"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#elif 指示詞"
  - "#else 指示詞"
  - "#endif 指示詞"
  - "#if 指示詞"
  - "條件式編譯, 指示詞"
  - "defined 指示詞"
  - "elif 指示詞 (#elif)"
  - "else 指示詞 (#else)"
  - "endif 指示詞 (#endif)"
  - "if 指示詞 (#if)"
  - "前置處理器, 指示詞"
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #if、#elif、#else 和 #endif 指示詞 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#if` 指示詞搭配 `#elif`、`#else` 和 `#endif` 指示詞可控制原始程式檔的部分編譯。  如果您撰寫的運算式 \(在 `#if` 之後\) 包含非零值，緊接在 `#if` 指示詞之後的折線圖組會保留在轉譯單位中。  
  
## 文法  
 *conditional* ：  
 *if\-part elif\-parts* opt *else\-part*opt *endif\-line*  
  
 *if\-part* ：  
 *if\-line text*  
  
 *if\-line* ：  
 **\#if**  *constant\-expression*  
  
 **\#ifdef**  *identifier*  
  
 **\#ifndef**  *identifier*  
  
 *elif\-parts* ：  
 *elif\-line text*  
  
 *elif\-parts elif\-line text*  
  
 *elif\-line* ：  
 **\#elif**  *constant\-expression*  
  
 *else\-part* ：  
 *else\-line 文字*  
  
 *else\-line* ：  
 `#else`  
  
 *endif\-line* ：  
 `#endif`  
  
 原始程式檔中的每個 `#if` 指示詞必須有相符的結尾 `#endif` 指示詞。  `#if` 和 `#endif` 指示詞之間可以出現任何數目的 `#elif` 指示詞，不過最多只允許一個 `#else` 指示詞。  `#else` 指示詞 \(如果有的話\) 必須是 `#endif` 之前的最後一個指示詞。  
  
 `#if`、`#elif`、`#else` 和 `#endif` 指示詞可以在其他 `#if` 指示詞的文字部分中形成巢狀結構。  每個巢狀 `#else`、`#elif` 或 `#endif` 指示詞都屬於前一個最接近的 `#if` 指示詞。  
  
 所有條件式編譯指示詞 \(例如 `#if` 和 **\#ifdef**\) 必須與檔案結尾之前的結尾 `#endif` 指示詞相符；否則會產生錯誤訊息。  當 Include 檔包含條件式編譯指示詞時，這些指示詞必須滿足相同的條件：include 檔結尾不可以有不相符的條件式編譯指示詞。  
  
 巨集取代是在命令列中 `#elif` 命令之後的部分中執行，因此巨集呼叫可用於 *constant\-expression*。  
  
 前置處理器會從指定出現次數的 *text* 選取一個，以供進一步處理。  *text* 中指定的區塊可以是任何文字序列。  可能會佔用一行以上。  *text* 通常是對編譯器或前置處理器有意義的程式文字。  
  
 前置處理器會處理選取的 *text* 並將其傳遞至編譯器。  如果 *text* 包含前置處理器指示詞，前置處理器會執行這些指示詞。  只會編譯前置處理器選取的文字區塊。  
  
 前置處理器會選取單一 *text* 項目，其方法是評估每個 `#if` 或 `#elif` 指示詞之後的常數運算式，直到找到評估為 true \(非零\) 的常數運算式為止。  它會選取直到其相關聯 `#elif`、`#else` 或 `#endif` 的所有文字 \(包括其他以 **\#** 開頭的前置處理器指示詞\)。  
  
 如果 *constant\-expression* 的所有項目都是 false，或者如果沒有任何 `#elif` 指示詞，前置處理器會選取 `#else` 子句之後的文字區塊。  如果省略 `#else` 子句，而且 `#if` 區塊中的 *constant\-expression* 的所有執行個體為 false，就不會選取文字區塊。  
  
 *constant\-expression* 是整數常數運算式，具有以下額外限制的：  
  
-   運算式必須是整數類型，而且只能包含整數常數、字元常數和 **defined** 運算子。  
  
-   運算式無法使用 `sizeof` 或類型轉換運算子。  
  
-   目標環境可能無法表示所有範圍的整數。  
  
-   轉譯表示 `int` 類型與 **long** 類型相同，而 `unsigned int` 與 `unsigned long` 相同。  
  
-   轉譯器可以將字元常數轉譯為一組與目標環境的一組程式碼值不同的程式碼值。  若要判斷目標環境的屬性，請於針對目標環境建置之應用程式的 LIMITS.H 中檢查巨集的值。  
  
-   運算式不得執行任何環境查詢，並且必須與目標電腦上的實作詳細資料保持隔離。  
  
 前置處理器運算子 **defined** 可用於特殊常數運算式，如下列語法所示：  
  
 defined\( `identifier` \)  
  
 defined `identifier`  
  
 如果 *identifier* 目前已定義，則將這個常數運算式視為 true \(非零\)；否則條件為 false \(0\)。  定義成空白文字的識別項會被視為已定義。  **defined** 指示詞可用於 `#if` 和 `#elif` 指示詞，此外就無處可用。  
  
 在下列範例中，`#if` 和 `#endif` 指示詞會控制三個函式呼叫之一的編譯：  
  
```  
#if defined(CREDIT)  
    credit();  
#elif defined(DEBIT)  
    debit();  
#else  
    printerror();  
#endif  
```  
  
 如果識別項 `CREDIT` 已定義，就會編譯 `credit` 的函式呼叫。  如果識別項 `DEBIT` 已定義，就會編譯 `debit` 的函式呼叫。  如果這些識別項都未定義，就會編譯 `printerror` 的呼叫。  請注意，`CREDIT` 與 `credit` 在 C 和 C\+\+ 中是不同的識別項，因為它們的大小寫不同。  
  
 在下列範例中的條件式編譯陳述式假設先前定義名為 `DLEVEL` 的符號常數。  
  
```  
#if DLEVEL > 5  
    #define SIGNAL  1  
    #if STACKUSE == 1  
        #define STACK   200  
    #else  
        #define STACK   100  
    #endif  
#else  
    #define SIGNAL  0  
    #if STACKUSE == 1  
        #define STACK   100  
    #else  
        #define STACK   50  
    #endif  
#endif  
#if DLEVEL == 0  
    #define STACK 0  
#elif DLEVEL == 1  
    #define STACK 100  
#elif DLEVEL > 5  
    display( debugptr );  
#else  
    #define STACK 200  
#endif  
```  
  
 第一個 `#if` 區塊顯示兩組巢狀 `#if`、`#else` 和 `#endif` 指示詞。  只有在 `DLEVEL > 5` 為 true 時，才會處理第一組指示詞。  否則，處理 \#**else** 之後的陳述式。  
  
 第二個範例中的 `#elif` 和 `#else` 指示詞會用來根據 `DLEVEL` 的值選擇四個選項之一。  常數 `STACK` 會設為 0、100 或 200，視 `DLEVEL` 的定義而定。  如果 `DLEVEL` 大於 5，則陳述式  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 會進行編譯且 `STACK` 未定義。  
  
 條件式編譯的常見用途是防止多次包含相同的標頭檔。  在 C\+\+ 中，類別通常是在標頭檔中定義，如下所列的建構可以用來防止多重定義：  
  
```  
/*  EXAMPLE.H - Example header file  */  
#if !defined( EXAMPLE_H )  
#define EXAMPLE_H  
  
class Example  
{  
...  
};  
  
#endif // !defined( EXAMPLE_H )  
```  
  
 上述程式碼會檢查符號常數 `EXAMPLE_H` 是否已定義。  如果是，檔案已包含且並不需要重新處理。  否則會定義常數 `EXAMPLE_H` 以便將 EXAMPLE.H 標記為已經處理。  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)