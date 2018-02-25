---
title: "#如果 #elif、 #else 和 #endif 指示詞 （C/c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
dev_langs:
- C++
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13a684412b0b0b24cbb9067ef6ea4cf78810c37f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if、#elif、#else 和 #endif 指示詞 (C/C++)
`#if` 指示詞搭配 `#elif`、`#else` 和 `#endif` 指示詞可控制原始程式檔的部分編譯。 如果您撰寫的運算式 (在 `#if` 之後) 包含非零值，緊接在 `#if` 指示詞之後的折線圖組會保留在轉譯單位中。  
  
## <a name="grammar"></a>文法  
 *條件式*:  
 *如果部分 elif 部分*選擇*else 部分*選擇*endif 列*  
  
 *如果部分*:  
 *如果行文字*  
  
 *如果行*:  
 **#if**  *constant-expression*  
  
 **#ifdef**  *identifier*  
  
 **#ifndef**  *identifier*  
  
 *elif 部分*:  
 *elif 行文字*  
  
 *elif 部分 elif 行文字*  
  
 *elif 列*:  
 **#elif**  *constant-expression*  
  
 *else 部分*:  
 *else-line 文字*  
  
 *其他列*:  
 `#else`  
  
 *endif 列*:  
 `#endif`  
  
 原始程式檔中的每個 `#if` 指示詞必須有相符的結尾 `#endif` 指示詞。 `#elif` 和 `#if` 指示詞之間可以出現任何數目的 `#endif` 指示詞，不過最多只允許一個 `#else` 指示詞。 `#else` 指示詞 (如果有的話) 必須是 `#endif` 之前的最後一個指示詞。  
  
 `#if`、`#elif`、`#else` 和 `#endif` 指示詞可以在其他 `#if` 指示詞的文字部分中形成巢狀結構。 每個巢狀 `#else`、`#elif` 或 `#endif` 指示詞都屬於前一個最接近的 `#if` 指示詞。  
  
 所有的條件式編譯指示詞，例如`#if`和**#ifdef**，必須符合與右`#endif`指示詞之前的檔案結尾; 否則會產生錯誤訊息。 當 Include 檔包含條件式編譯指示詞時，這些指示詞必須滿足相同的條件：include 檔結尾不可以有不相符的條件式編譯指示詞。  
  
 命令列所示的組件內執行的巨集取代`#elif`命令，因此可用於巨集呼叫*常數運算式*。  
  
 前置處理器會選取其中一個指定的出現次數的*文字*以便進一步處理。 中指定的區塊*文字*可以是任何文字序列。 可能會佔用一行以上。 通常*文字*是有意義的編譯器或前置處理器的程式文字。  
  
 前置處理器會處理選取*文字*並將其傳遞給編譯器。 如果*文字*包含前置處理器指示詞，前置處理器會執行這些指示詞。 只會編譯前置處理器選取的文字區塊。  
  
 前置處理器會選取單一*文字*藉由評估每個常數運算式的項目`#if`或`#elif`指示詞，直到找到，則為 true （非零） 的常數運算式。 它會選取所有文字 (包括其他開頭的前置處理器指示詞 **#** ) 至其相關聯`#elif`， `#else`，或`#endif`。  
  
 如果所有發生次數*常數運算式*都是 false，或者如果沒有任何`#elif`指示詞，前置處理器會選取之後的文字區塊`#else`子句。 如果`#else`省略子句的所有執行個體和*常數運算式*中`#if`區塊，則為 false，會選取任何文字區塊。  
  
 *常數運算式*是整數常數運算式具有以下額外限制：  
  
-   運算式必須有整數類資料類型，而且可以包含整數常數、 字元常數和**定義**運算子。  
  
-   運算式無法使用 `sizeof` 或類型轉換運算子。  
  
-   目標環境可能無法表示所有範圍的整數。  
  
-   轉譯表示型別`int`型別相同**長**，和`unsigned int`相同`unsigned long`。  
  
-   轉譯器可以將字元常數轉譯為一組與目標環境的一組程式碼值不同的程式碼值。 若要判斷目標環境的屬性，請於針對目標環境建置之應用程式的 LIMITS.H 中檢查巨集的值。  
  
-   運算式不得執行任何環境查詢，並且必須與目標電腦上的實作詳細資料保持隔離。  

## <a name="defined"></a>已定義的  
 前置處理器運算子**定義**可以用於特殊常數運算式，如以下語法所示：  
  
 defined( `identifier` )  
  
 defined `identifier`  
  
 這個常數運算式視為 true （非零），是否*識別碼*目前定義; 否則條件為 false (0)。 定義成空白文字的識別項會被視為已定義。 **定義**指示詞可用於`#if`和`#elif`指示詞，但其他無處可去。  
  
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
  
 如果識別項 `credit` 已定義，就會編譯 `CREDIT` 的函式呼叫。 如果識別項 `DEBIT` 已定義，就會編譯 `debit` 的函式呼叫。 如果這些識別項都未定義，就會編譯 `printerror` 的呼叫。 請注意，`CREDIT` 與 `credit` 在 C 和 C++ 中是不同的識別項，因為它們的大小寫不同。  
  
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
  
 第一個 `#if` 區塊顯示兩組巢狀 `#if`、`#else` 和 `#endif` 指示詞。 只有在 `DLEVEL > 5` 為 true 時，才會處理第一組指示詞。 否則，# 後面的陳述式**else**處理。  
  
 第二個範例中的 `#elif` 和 `#else` 指示詞會用來根據 `DLEVEL` 的值選擇四個選項之一。 常數 `STACK` 會設為 0、100 或 200，視 `DLEVEL` 的定義而定。 如果 `DLEVEL` 大於 5，則陳述式  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 會進行編譯且 `STACK` 未定義。  
  
 條件式編譯的常見用途是防止多次包含相同的標頭檔。 在 C++ 中，類別通常是在標頭檔中定義，如下所列的建構可以用來防止多重定義：  
  
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
  
 上述程式碼會檢查符號常數 `EXAMPLE_H` 是否已定義。 如果是，檔案已包含且並不需要重新處理。 否則會定義常數 `EXAMPLE_H` 以便將 EXAMPLE.H 標記為已經處理。  

## <a name="hasinclude"></a>__has_include
**Visual Studio 2017 15.3 和更新版本**： 判斷是否可以加入程式庫標頭：  

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```
  
## <a name="see-also"></a>請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)