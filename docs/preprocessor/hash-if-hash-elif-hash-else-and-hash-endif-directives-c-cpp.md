---
title: '#如果 #elif、 #else 和 #endif 指示詞 (C /C++)'
ms.date: 11/04/2016
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
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
ms.openlocfilehash: 90fbab45c6408c30198c2a52a42545718002cc11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409885"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if、#elif、#else 和 #endif 指示詞 (C/C++)

**#If**指示詞，搭配 **#elif**， **#else**，以及 **#endif**指示詞，控制項的原始程式檔部分編譯。 如果您撰寫的運算式 (之後 **#if**) 有非零值，緊接的折線圖組 **#if**指示詞會保留在轉譯單位中。

## <a name="grammar"></a>文法

*條件式*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if 部分 elif 部分*<sub>opt</sub> *else 部分*<sub>選擇</sub> *endif 列*

*if-part* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*如果行文字*

*if 程式行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if**  *constant-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef**  *identifier*

*elif 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif 行文字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif 部分 elif 單行文字*

*elif 列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif**  *constant-expression*

*else 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*else-line 文字*

*其他列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif 列*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

每個 **#if**原始程式檔中的指示詞必須比對的結尾 **#endif**指示詞。 任意數目的 **#elif**指示詞之間可以出現 **#if**並 **#endif**指示詞，但最多一個 **#else**允許指示詞。 **#Else**指示詞，如果有的話，必須是之前的最後一個指示詞 **#endif**。

**#If**， **#elif**， **#else**，以及 **#endif**指示詞可以巢狀在其他的文字部分 **#if**指示詞。 每個巢狀 **#else**， **#elif**，或 **#endif**指示詞都屬於前一個最接近 **#if**指示詞。

所有的條件式編譯指示詞，例如 **#if**並 **#ifdef**，結尾必須符合 **#endif**在檔案結尾; 之前的指示詞，否則為錯誤會產生訊息。 當條件式編譯指示詞內包含的檔案，它們必須滿足相同的條件：必須要有任何不相符的條件式編譯指示詞結尾的 include 檔。

巨集取代會在命令列後面的部分 **#elif**命令，因此可以使用巨集呼叫*常數運算式*。

前置處理器會選取其中一個指定的出現次數*文字*供進一步處理。 中指定的區塊*文字*可以是任何文字序列。 可能會佔用一行以上。 通常*文字*是對編譯器或前置處理器有意義的程式文字。

前置處理器會處理所選*文字*並將它傳遞給編譯器。 如果*文字*包含前置處理器指示詞，前置處理器會執行，這些指示詞。 只會編譯前置處理器選取的文字區塊。

前置處理器會選取單一*文字*藉由評估每個常數運算式的項目 **#if**或是 **#elif**指示詞，直到找到，則為 true （非零值） 常數運算式。 它會選取所有文字 (包括其他開頭的前置處理器指示詞**#**) 直到其相關聯 **#elif**， **#else**，或 **#endif**.

如果所有發生次數*常數運算式*都是 false，或者如果沒有任何 **#elif**指示詞，前置處理器會選取文字區塊之後 **#else**子句。 如果 **#else**省略子句的所有執行個體*常數運算式*中 **#if**區塊為 false，就會選取任何文字區塊。

*常數運算式*是整數常數運算式具有以下額外限制：

- 運算式必須有整數類資料類型，而且可以包含整數常數、 字元常數，而**定義**運算子。

- 運算式無法使用 `sizeof` 或類型轉換運算子。

- 目標環境可能無法表示所有範圍的整數。

- 轉譯表示型別**int**型別相同**長**，並**不帶正負號的 int**相同**不帶正負號長**。

- 轉譯器可以將字元常數轉譯為一組與目標環境的一組程式碼值不同的程式碼值。 若要判斷目標環境的屬性，請於針對目標環境建置之應用程式的 LIMITS.H 中檢查巨集的值。

- 運算式不得執行任何環境查詢，並且必須與目標電腦上的實作詳細資料保持隔離。

## <a name="defined"></a>已定義的

前置處理器運算子**定義**用於特殊常數運算式，如下列語法所示：

defined( `identifier` )

defined `identifier`

這個常數運算式視為 true （非零），是否*識別碼*目前定義; 否則條件為 false (0)。 定義成空白文字的識別項會被視為已定義。 **定義**指示詞可用於 **#if**並 **#elif**指示詞，但沒地方可繼續。

在下列範例中， **#if**並 **#endif**指示詞會控制編譯的三個函式呼叫的其中一個：

```C
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

```C
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

第一個 **#if**區塊顯示兩組巢狀 **#if**， **#else**，以及 **#endif**指示詞。 只有在 `DLEVEL > 5` 為 true 時，才會處理第一組指示詞。 否則之後, 的陳述式 **#else**處理。

**#Elif**並 **#else**第二個範例中的指示詞用來讓四個選項之一，根據值`DLEVEL`。 常數 `STACK` 會設為 0、100 或 200，視 `DLEVEL` 的定義而定。 如果 `DLEVEL` 大於 5，則陳述式

```C
#elif DLEVEL > 5
display(debugptr);
```

會進行編譯且 `STACK` 未定義。

條件式編譯的常見用途是防止多次包含相同的標頭檔。 在 C++ 中，類別通常是在標頭檔中定義，如下所列的建構可以用來防止多重定義：

```cpp
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

**Visual Studio 2017 15.3 版和更新版本**：判斷是否可以加入程式庫標頭：

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

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)