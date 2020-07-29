---
title: '#if、#elif、#else 和 #endif 指示詞 (C/C++)'
ms.date: 08/29/2019
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
ms.openlocfilehash: acbc54a80573bbbf29ad5cf67e7e5fd9351eeaa3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231594"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if、#elif、#else 和 #endif 指示詞（C/c + +）

具有 **#elif**、 **#else**和 **#endif**指示詞的 **#if**指示詞，會控制原始檔部分的編譯。 如果您撰寫的運算式（在 **#if**之後）具有非零值，則緊接在 **#if**指示詞之後的行群組會保留在轉譯單位中。

## <a name="grammar"></a>文法

*條件*式： \
&nbsp;&nbsp;&nbsp;&nbsp;*if-part elif part*<sub>opt</sub> *else-part*<sub>opt</sub> *endif-line*

*if-part* ： \
&nbsp;&nbsp;&nbsp;&nbsp;*if-line text*

*如果-line* ： \
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *常數運算式*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *識別碼*\
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *識別碼*

*elif-元件*： \
&nbsp;&nbsp;&nbsp;&nbsp;*elif 行文字*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-part elif-line text*

*elif-line* ： \
&nbsp;&nbsp;&nbsp;&nbsp;**#elif**  *常數運算式*

*else-part* ： \
&nbsp;&nbsp;&nbsp;&nbsp;*else-行文字*

*else-line* ： \
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif-line* ： \
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

## <a name="remarks"></a>備註

原始程式檔中的每個 **#if**指示詞都必須以結尾的 **#endif**指示詞進行比對。 **#If**和 **#endif**指示詞之間可以出現任意數目的 **#elif**指示詞，但最多隻允許一個 **#else**指示詞。 **#Else**指示詞（如果有的話）必須是 **#endif**前的最後一個指示詞。

**#If**、 **#elif**、 **#else**和 **#endif**指示詞可以在其他 **#if**指示詞的*文字*部分中加以嵌套。 每個嵌套的 **#else**、 **#elif**或 **#endif**指示詞都屬於最接近的前面 **#if**指示詞。

所有條件式編譯指示詞（例如 **#if**和 **#ifdef**）都必須符合檔案結尾之前的結尾 **#endif**指示詞。 否則，就會產生錯誤訊息。 當 Include 檔包含條件式編譯指示詞時，這些指示詞必須滿足相同的條件：include 檔結尾不可以有不相符的條件式編譯指示詞。

宏取代是在 **#elif**命令後面的那一行中完成，因此，可以在*常數運算式*中使用宏呼叫。

預處理器會選取其中一個指定的*文字*，以進行進一步的處理。 *文字*中指定的區塊可以是任何文字序列。 可能會佔用一行以上。 *文字*通常是對編譯器或預處理器具有意義的程式文字。

預處理器會處理選取的*文字*，並將它傳遞給編譯器。 如果*文字*包含預處理器指示詞，則預處理器會執行這些指示詞。 只會編譯前置處理器選取的文字區塊。

預處理器會藉由評估每個 **#if**或 **#elif**指示詞之後的常數運算式來選取單一*文字*專案，直到找到 true （非零）常數運算式為止。 它會從 **#** 其相關聯的 **#elif**、 **#else**或 **#endif**選取所有文字（包括以開頭的其他預處理器指示詞）。

如果所有出現的*常數運算式*都是 false，或如果沒有出現 **#elif**指示詞，則預處理器會在 **#else**子句之後選取文字區塊。 當沒有 **#else**子句，而且 **#if**區塊中的所有*常數運算式*實例都是 false 時，就不會選取任何文字區塊。

*常數運算式*是具有下列額外限制的整數常數運算式：

- 運算式必須有整數類資料類型，而且只能包含整數常數、字元常數和**已定義**的運算子。

- 運算式不能使用 **`sizeof`** 或類型轉換運算子。

- 目標環境可能無法代表所有的整數範圍。

- 翻譯所代表的類型與 **`int`** 類型相同 **`long`** ，其方式與 **`unsigned int`** 相同 **`unsigned long`** 。

- 轉譯器可以將字元常數轉譯為一組與目標環境的一組程式碼值不同的程式碼值。 若要判斷目標環境的屬性，請使用針對該環境所建立的應用程式來檢查限制的值 *。H*宏。

- 運算式不能查詢環境，而且必須與目的電腦上的執行詳細資料保持不變。

## <a name="preprocessor-operators"></a>前置處理器運算子

### <a name="defined"></a>已定義

**定義**的預處理器運算子可以在特殊常數運算式中使用，如下列語法所示：

> **已定義（** *識別碼* **）**\
> **已定義** *識別碼*

如果目前已定義*識別碼*，這個常數運算式就會被視為 true （非零）。 否則，條件為 false (0)。 定義成空白文字的識別項會被視為已定義。 **定義**的運算子可以用在 **#if**和 **#elif**指示詞中，但其他地方則不適用。

在下列範例中， **#if**和 **#endif**指示詞會控制三個函式呼叫之一的編譯：

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

如果識別項 `credit` 已定義，就會編譯 `CREDIT` 的函式呼叫。 如果識別項 `DEBIT` 已定義，就會編譯 `debit` 的函式呼叫。 如果這些識別項都未定義，就會編譯 `printerror` 的呼叫。 `CREDIT`和 `credit` 都是 c 和 c + + 中的相異識別碼，因為它們的大小寫不同。

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

第一個 **#if**區塊會顯示兩組嵌套的 **#if**、 **#else**和 **#endif**指示詞。 只有在 `DLEVEL > 5` 為 true 時，才會處理第一組指示詞。 否則，會處理 **#else**之後的語句。

第二個範例中的 **#elif**和 **#else**指示詞，是用來根據的值進行四個選擇之一 `DLEVEL` 。 常數 `STACK` 會設為 0、100 或 200，視 `DLEVEL` 的定義而定。 如果 `DLEVEL` 大於 5，則陳述式

```C
#elif DLEVEL > 5
display(debugptr);
```

已編譯，且 `STACK` 未定義。

條件式編譯的常見用途是防止多次包含相同的標頭檔。 在 c + + 中，類別通常會定義在標頭檔中，這類的結構可以用來防止多個定義：

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

上述程式碼會檢查符號常數 `EXAMPLE_H` 是否已定義。 若是如此，就已經包含檔案，而且不需要重新處理。 否則會定義常數 `EXAMPLE_H` 以便將 EXAMPLE.H 標記為已經處理。

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 15.3 版和更新**版本：判斷是否有程式庫標頭可供包含：

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
