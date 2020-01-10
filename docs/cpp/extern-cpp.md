---
title: extern （C++）
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: d42a32202f7fa67751ea36757c13b2c6af4953b2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301531"
---
# <a name="extern-c"></a>extern （C++）

**Extern**關鍵字會套用至全域變數、函式或樣板宣告，以指定該內容的名稱具有*外部連結*。 如需連結的背景資訊，以及為什麼不鼓勵使用全域變數，請參閱[轉譯單位和連結](program-and-linkage-cpp.md)。

視內容而定， **extern**關鍵字具有四個意義：

1. 在非 const 全域變數宣告中， **extern**指定變數或函式定義于另一個轉譯單位中。 **外部**必須套用在定義變數的所有檔案中。
1. 在 const 變數宣告中，它會指定變數具有外部連結。 **外部**必須套用至所有檔案中的所有宣告。 （全域 const 變數預設具有內部連結）。
1. **extern "C"** 指定函式定義于其他地方，並使用 C 語言呼叫慣例。 Extern "C" 修飾詞也可以套用至區塊中的多個函式宣告。
1. 在範本宣告中，它會指定範本已在其他位置具現化。 這是一項優化，告訴編譯器它可以重複使用另一個具現化，而不是在目前的位置建立一個新的。 如需有關此**外部**使用的詳細資訊，請參閱[範本](templates-cpp.md)。

## <a name="extern-linkage-for-non-const-globals"></a>非 const globals 的 extern 連結

當連結器在全域變數宣告之前看到**extern**時，它會在另一個轉譯單位中尋找定義。 全域範圍內的非 const 變數宣告預設為外部;僅將**extern**套用至未提供定義的宣告。

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

## <a name="extern-linkage-for-const-globals"></a>const globals 的 extern 連結

**Const** global 變數預設具有內部連結。 如果您想要讓變數具有外部連結，請將**extern**關鍵字套用至定義，並將其他檔案中的所有其他宣告套用至：

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>extern constexpr 連結

在 Visual Studio 2017 15.3 版和更早版本中，即使變數已標記為 extern，編譯器一律會提供 constexpr 變數內部連結。 在 Visual Studio 2017 15.5 版中，新的編譯器參數 ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) 讓行為可正確且符合標準。 這最後終究會成為預設值。 /Permissive-選項不會啟用/Zc： externConstexpr。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果標頭檔包含宣告為 extern constexpr 的變數，則必須將它標記為 **__declspec （selectany）** ，才能正確地結合其重複宣告：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>extern "C" 和 extern "C++" 函式宣告

在C++中，當與字串搭配使用時， **extern**會指定將另一種語言的連結慣例用於宣告子。 只有在先前宣告為具有 C 連結時，才可以存取 C 函式和資料。 不過，您必須在另行編譯的轉譯單位中定義它們。

Microsoft C++支援*字串常*值欄位中的字串 **"C"** 和**C++""** 。 所有標準 include 檔都使用**extern** "C" 語法，以允許在程式中C++使用執行時間程式庫函數。

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

如果函式具有多個連結規格，這些規格必須一致；將函式宣告為同時具有 C 和 C++ 連結是錯誤的。 此外，如果程式中的一個函式發生兩次宣告 (一個使用連結規格，另一個沒有)，則使用連結規格的宣告必須是第一個。 第一個宣告會針對任何已經有連結規格的其餘函式宣告指定連結。 例如：

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

[關鍵字](../cpp/keywords-cpp.md)<br/>
[轉譯單位和連結](program-and-linkage-cpp.md)<br/>
[C 中的 extern 儲存類別規範](../c-language/extern-storage-class-specifier.md)<br/>
[C 中的識別碼行為](../c-language/behavior-of-identifiers.md)<br/>
[C 中的連結](../c-language/linkage.md)