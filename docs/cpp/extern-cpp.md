---
title: :::no-loc(extern):::C + +
description: 'C + + 語言 :::no-loc(extern)::: 關鍵字指南。'
ms.date: 01/28/2020
f1_keywords:
- ':::no-loc(extern):::'
- :::no-loc(extern):::_CPP
helpviewer_keywords:
- ':::no-loc(extern)::: keyword [C++], linkage to non-C++ functions'
- declarations, :::no-loc(extern):::al
- ':::no-loc(extern):::al linkage, :::no-loc(extern)::: modifier'
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- ':::no-loc(extern):::'
- ':::no-loc(const):::'
- ':::no-loc(constexpr):::'
- ':::no-loc(permissive):::'
ms.openlocfilehash: 510352f9e99e513f4a426f6ef89be4474085d97c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227500"
---
# <a name="no-locextern-c"></a>:::no-loc(extern):::C + +

**`:::no-loc(extern):::`** 關鍵字可以套用至全域變數、函式或範本宣告。 它會指定符號具有* :::no-loc(extern)::: al 連結*。 如需連結的背景資訊，以及為什麼不鼓勵使用全域變數，請參閱[轉譯單位和連結](program-and-linkage-cpp.md)。

根據內容而定， **`:::no-loc(extern):::`** 關鍵字具有四個意義：

- 在非 **`:::no-loc(const):::`** 全域變數宣告中， **`:::no-loc(extern):::`** 指定變數或函式定義于另一個轉譯單位中。 **`:::no-loc(extern):::`** 除了定義變數的檔案以外，必須套用在所有檔案中。

- 在變數宣告中 **`:::no-loc(const):::`** ，它會指定變數具有 :::no-loc(extern)::: al 連結。 **`:::no-loc(extern):::`** 必須套用至所有檔案中的所有宣告。 （全域 **`:::no-loc(const):::`** 變數預設具有內部連結）。

- ** :::no-loc(extern)::: "C"** 指定函式定義于其他地方，並使用 C 語言呼叫慣例。 :::no-loc(extern):::"C" 修飾詞也可以套用至區塊中的多個函式宣告。

- 在範本宣告中， **`:::no-loc(extern):::`** 指定範本已在其他位置具現化。 **`:::no-loc(extern):::`** 告訴編譯器它可以重複使用另一個具現化，而不是在目前的位置建立一個新的實例。 如需有關此使用的詳細資訊 **`:::no-loc(extern):::`** ，請參閱明確具現[化](explicit-instantiation.md)。

## <a name="no-locextern-linkage-for-non-no-locconst-globals"></a>:::no-loc(extern):::非 globals 的連結 :::no-loc(const):::

當連結器在 **`:::no-loc(extern):::`** 全域變數宣告之前看到時，它會在另一個轉譯單位中尋找定義。 全域範圍中非 **`:::no-loc(const):::`** 變數的宣告預設為 :::no-loc(extern)::: al。 僅適用于 **`:::no-loc(extern):::`** 未提供定義的宣告。

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileC.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
:::no-loc(extern)::: int i = 43; // same error (:::no-loc(extern)::: is ignored on definitions)
```

## <a name="no-locextern-linkage-for-no-locconst-globals"></a>:::no-loc(extern):::globals 的連結 :::no-loc(const):::

**`:::no-loc(const):::`** 全域變數預設具有內部連結。 如果您想要讓變數具有 :::no-loc(extern)::: al 連結，請將 **`:::no-loc(extern):::`** 關鍵字套用至定義，並套用至其他檔案中的所有其他宣告：

```cpp
//fileA.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i = 42; // :::no-loc(extern)::: :::no-loc(const)::: definition

//fileB.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i;  // declaration only. same as i in FileA
```

## <a name="no-locextern-no-locconstexpr-linkage"></a>:::no-loc(extern)::::::no-loc(constexpr):::連結

在 Visual Studio 2017 15.3 版和更早版本中，編譯器一律會提供 **`:::no-loc(constexpr):::`** 變數內部連結，即使變數已標記也一樣 **`:::no-loc(extern):::`** 。 在 Visual Studio 2017 15.5 版和更新版本中， [/zc： :::no-loc(extern)::: Constexpr](../build/reference/zc-:::no-loc(extern)::::::no-loc(constexpr):::.md)編譯器參數會啟用符合標準的正確行為。 最後，選項會變成預設值。 此 [/:::no-loc(permissive):::-](../build/reference/:::no-loc(permissive):::-standards-conformance.md) 選項不會啟用 **/Zc： :::no-loc(extern)::: Constexpr**。

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: int x = 10; //error LNK2005: "int :::no-loc(const)::: x" already defined
```

如果標頭檔包含宣告的變數 **`:::no-loc(extern):::`** **`:::no-loc(constexpr):::`** ，則必須將它標記 `__declspec(selectany)` 為正確地結合其重複宣告：

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: __declspec(selectany) int x = 10;
```

## <a name="no-locextern-c-and-no-locextern-c-function-declarations"></a>:::no-loc(extern):::"C" 和 :::no-loc(extern)::: "c + +" 函式宣告

在 c + + 中，搭配字串使用時， **`:::no-loc(extern):::`** 會指定將另一種語言的連結慣例用於宣告子。 只有當 c 函式和資料先前宣告為具有 C 連結時，才能加以存取。 不過，您必須在另行編譯的轉譯單位中定義它們。

Microsoft c + + 支援*字串常*值欄位中的字串 **"C"** 和 **"c + +"** 。 所有標準 include 檔都使用** :::no-loc(extern)::: "c"** 語法，以允許在 c + + 程式中使用執行時間程式庫函數。

## <a name="example"></a>範例

下列範例顯示如何宣告具有 C 連結的名稱：

```cpp
// Declare printf with C linkage.
:::no-loc(extern)::: "C" int printf(:::no-loc(const)::: char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
:::no-loc(extern)::: "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
:::no-loc(extern)::: "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
:::no-loc(extern)::: "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

:::no-loc(extern)::: "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
:::no-loc(extern)::: "C" int errno;
```

如果函式有一個以上的連結規格，則必須同意。 將函式宣告為同時具有 C 和 c + + 連結是錯誤的。 此外，如果程式中的一個函式發生兩次宣告 (一個使用連結規格，另一個沒有)，則使用連結規格的宣告必須是第一個。 第一個宣告會針對任何已經有連結規格的其餘函式宣告指定連結。 例如：

```cpp
:::no-loc(extern)::: "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
:::no-loc(extern)::: "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>另請參閱

[字](../cpp/keywords-cpp.md)\
[轉譯單位和連結](program-and-linkage-cpp.md)\
[:::no-loc(extern):::C 中的儲存類別規範](../c-language/:::no-loc(extern):::-storage-class-specifier.md)\
[C 中的識別碼行為](../c-language/behavior-of-identifiers.md)\
[C 中的連結](../c-language/linkage.md)
