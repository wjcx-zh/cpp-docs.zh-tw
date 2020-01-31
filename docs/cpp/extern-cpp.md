---
title: extern （C++）
description: Language extern 關鍵字C++的指南。
ms.date: 01/28/2020
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- extern
- const
- constexpr
- permissive
ms.openlocfilehash: 422b6960802c59f1c45e0c22a4a85988c808a5b3
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821762"
---
# <a name="opno-locextern-c"></a>extern （C++）

**extern** 關鍵字可以套用至全域變數、函式或範本宣告。 它會指定符號具有*外部連結*。 如需連結的背景資訊，以及為什麼不鼓勵使用全域變數，請參閱[轉譯單位和連結](program-and-linkage-cpp.md)。

視內容而定， **extern** 關鍵字具有四個意義：

- 在非 **const** 的全域變數宣告中， **extern** 指定變數或函式定義于另一個轉譯單位中。 除了定義變數的檔案以外，必須在所有檔案中套用 **extern** 。

- 在 **const** 變數宣告中，它會指定變數具有外部連結。 **extern** 必須套用至所有檔案中的所有宣告。 （全域 **const** 變數預設具有內部連結）。

- **extern "C"** 指定函式定義于其他地方，並使用 C 語言呼叫慣例。 extern "C" 修飾詞也可以套用至區塊中的多個函式宣告。

- 在樣板宣告中， **extern** 指定範本已在其他位置具現化。 **extern** 告訴編譯器它可以重複使用另一個具現化，而不是在目前的位置建立新的實例。 如需有關這項 **extern** 使用的詳細資訊，請參閱明確具現[化](explicit-instantiation.md)。

## <a name="opno-locextern-linkage-for-non-opno-locconst-globals"></a>非const 的全域 extern 連結

當連結器在全域變數宣告之前看到 **extern** 時，它會在另一個轉譯單位中尋找定義。 全域範圍內非 **const** 變數的宣告預設為外部。 僅將 **extern** 套用至未提供定義的宣告。

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="opno-locextern-linkage-for-opno-locconst-globals"></a>const globals 的 extern 連結

**const** 的全域變數預設具有內部連結。 如果您想要讓變數具有外部連結，請將 **extern** 關鍵字套用至定義，並套用至其他檔案中的所有其他宣告：

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="opno-locextern-opno-locconstexpr-linkage"></a>extern constexpr 連結

在 Visual Studio 2017 15.3 版和更早版本中，編譯器一律會提供 **constexpr** 變數內部連結，即使變數已標記為 **extern** 也一樣。 在 Visual Studio 2017 15.5 版和更新版本中， [/zc： externConstexpr](../build/reference/zc-externconstexpr.md)編譯器參數會啟用符合標準的正確行為。 最後，選項會變成預設值。 [/permissive-](../build/reference/permissive-standards-conformance.md)選項不會啟用 **/zc： externConstexpr**。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果標頭檔包含 **extern** **constexpr** 宣告的變數，則必須將它標記為 `__declspec(selectany)`，才能正確地合併其重複宣告：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="opno-locextern-c-and-opno-locextern-c-function-declarations"></a>extern "C" 和 extern "C++" 函式宣告

在C++中，當與字串搭配使用時， **extern** 指定將另一種語言的連結慣例用於宣告子。 只有當 c 函式和資料先前宣告為具有 C 連結時，才能加以存取。 不過，您必須在另行編譯的轉譯單位中定義它們。

Microsoft C++支援*字串常*值欄位中的字串 **"C"** 和**C++""** 。 所有標準 include 檔都使用 **extern "C"** 語法，以允許在程式中C++使用執行時間程式庫函數。

## <a name="example"></a>範例

下列範例顯示如何宣告具有 C 連結的名稱：

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

如果函式有一個以上的連結規格，則必須同意。 將函式宣告為同時具有 C 和C++連結是錯誤的。 此外，如果程式中的一個函式發生兩次宣告 (一個使用連結規格，另一個沒有)，則使用連結規格的宣告必須是第一個。 第一個宣告會針對任何已經有連結規格的其餘函式宣告指定連結。 例如：

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>請參閱

[關鍵字](../cpp/keywords-cpp.md)\
[轉譯單位和連結](program-and-linkage-cpp.md)\
[C\ 中extern 儲存類別規範](../c-language/extern-storage-class-specifier.md)
[C\ 中的識別碼行為](../c-language/behavior-of-identifiers.md)
[C 中的連結](../c-language/linkage.md)
