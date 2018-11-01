---
title: extern （c + +）
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: 4a3a4e158794e06f28c638e87e014ddc3fb99837
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648717"
---
# <a name="extern-c"></a>extern （c + +）

**Extern**關鍵字是否套用至指定的名稱具有全域變數、 函式或樣板宣告*外部連結*。 如需連結和為什麼使用全域變數，否則不建議的背景資訊，請參閱[程式和連結](program-and-linkage-cpp.md)。

**Extern**關鍵字有四個意義視內容而定：

1. 在非 const 全域變數宣告中， **extern**指定變數或函式在另一個轉譯單位中定義。 **Extern**必須套用在其中定義的變數以外所有的檔案。
1. 在 const 變數宣告中，它會指定該變數具有外部連結。 **Extern**必須套用到所有的檔案中的所有宣告。 （全域的 const 變數會具有內部連結的預設值）。
1. **extern"C"** 指定函式在其他地方定義，並使用 C 語言的呼叫慣例。 Extern"C"修飾詞也可能會套用至多個區塊中的函式宣告。
1. 在範本宣告中，它會指定，範本已經產生其他位置。 這是會告知編譯器，它可以重複使用其他具現化，而不是建立一個新的目前位置的最佳化。 如需有關此善用**extern**，請參閱[範本](templates-cpp.md)。

## <a name="extern-linkage-for-non-const-globals"></a>非 const 的全域的外部連結

當連結器看到**extern**全域變數宣告之前，它會尋找另一個轉譯單位中的定義。 在全域範圍的非 const 變數的宣告式預設為外部;僅適用於**extern**不提供定義宣告。

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

## <a name="extern-linkage-for-const-globals"></a>const 的全域變數的外部連結

A **const**預設全域變數具有內部連結。 如果您想要具有外部連結的變數時，套用**extern**關鍵字加入定義以及其他檔案中的所有其他宣告有關：

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>extern constexpr 連結

在 Visual Studio 2017 15.3 和更早版本，編譯器一律會指定 constexpr 變數內部連結即使變數已標示為 extern。 在 Visual Studio 2017 15.5 版中，新的編譯器參數 ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) 讓行為可正確且符合標準。 這最後終究會成為預設值。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

如果標頭檔包含變數的宣告的 extern constexpr，它必須標示 **__declspec （selectany)** 才能正確地合併其重複宣告：

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>extern"C"和 extern"C + +"函式宣告

C + + 中為字串，搭配使用時**extern**指定另一種語言的連接慣例用於宣告子使用。 只有在先前宣告為具有 C 連結時，才可以存取 C 函式和資料。 不過，您必須在另行編譯的轉譯單位中定義它們。

Microsoft c + + 支援字串 **"C"** 並 **「 c + +"** 中*字串常值*欄位。 所有標準，包括檔案使用**extern** "C"語法，以允許使用 c + + 程式中的執行階段程式庫函式。

## <a name="example"></a>範例

下列範例示範如何宣告具有 C 連結的名稱：

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

如果函式具有多個連結規格，這些規格必須一致；將函式宣告為同時具有 C 和 C++ 連結是錯誤的。 此外，如果程式中的一個函式發生兩次宣告 (一個使用連結規格，另一個沒有)，則使用連結規格的宣告必須是第一個。 第一個宣告會針對任何已經有連結規格的其餘函式宣告指定連結。 例如: 

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

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[程式和連結](program-and-linkage-cpp.md)<br/>
[extern 儲存類別規範 c](../c-language/extern-storage-class-specifier.md)<br/>
[在 C 中的識別項的行為](../c-language/behavior-of-identifiers.md)<br/>
[在 C 中的連結](../c-language/linkage.md)