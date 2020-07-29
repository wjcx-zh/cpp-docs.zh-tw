---
title: C++ 語言參考
ms.custom: index-page
ms.date: 12/10/2019
helpviewer_keywords:
- C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
ms.openlocfilehash: 7b0d1227419aef3174d4f18b11cdc334879383b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221740"
---
# <a name="c-language-reference"></a>C++ 語言參考

本參考說明在 Microsoft c + + 編譯器中實作為 c + + 程式設計語言。 組織是根據 Margaret Ellis 和 Bjarne Stroustrup 以及 ANSI/ISO c + + 國際標準（ISO/IEC FDIS 14882）上*標注的 c + + 參考手冊*。 已包含 Microsoft 專有 C++ 語言功能實作。

如需現代化 c + + 程式設計實務的總覽，請參閱[歡迎回到 c + +](welcome-back-to-cpp-modern-cpp.md)。

請參閱下表，快速尋找關鍵字或運算子：

- [C + + 關鍵字](../cpp/keywords-cpp.md)

- [C + + 運算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>本節內容

[詞法慣例](../cpp/lexical-conventions.md)<br/>
C ++ 程式的基本語彙元素：語彙基元、註解、運算子、關鍵字、標點符號、常值。 另外還有檔案轉譯、運算子優先順序/關聯性。

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
範圍、連結、程式啟動和結束、儲存類別以及類型。

[內建類型](fundamental-types-cpp.md)C + + 編譯器和其值範圍內建的基本類型。

[標準轉換](../cpp/standard-conversions.md)<br/>
內建類型之間的類型轉換。 另外還有算術轉換，以及指標、參考與成員指標類型之間的轉換。

宣告[和定義](declarations-and-definitions-cpp.md)宣告和定義變數、類型和函數。

[運算子、優先順序及關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
C++ 中的運算子。

[運算式](../cpp/expressions-cpp.md)<br/>
運算式類型、運算式語意、運算子參考主題、轉型和轉型運算子、執行階段類型資訊。

[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)<br/>
程式設計技巧，可隱含定義函式物件類別和建構該類別類型的函式物件。

[陳述式](../cpp/statements-cpp.md)<br/>
運算式、null、複合、選取、反覆項目、跳躍和宣告陳述式。

[類別和結構](../cpp/classes-and-structs-cpp.md)<br/>
類別、結構和等位簡介。 此外，成員函式、特殊成員函式、資料成員、位欄位、 **`this`** 指標、嵌套類別。

[等位](unions.md)<br/>
使用者定義的類型，其中所有成員都會共用相同的記憶體位置。

[衍生類別](../cpp/inheritance-cpp.md)<br/>
單一和多重繼承、 **`virtual`** 函數、多個基類、**抽象**類、範圍規則。 此外， **`__super`** 和 **`__interface`** 關鍵字。

[成員存取控制](../cpp/member-access-control-cpp.md)<br/>
控制對類別成員的存取： **`public`** 、 **`private`** 和 **`protected`** 關鍵字。 Friend 函式和類別。

[多載化](operator-overloading.md)<br/>
多載運算子，運算子多載的規則。

[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)<br/>
C++ 例外狀況處理、結構化例外狀況處理 (SEH)、用於撰寫例外狀況處理陳述式的關鍵字。

[判斷提示和使用者提供的訊息](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error`指示詞、 **`static_assert`** 關鍵字、 `assert` 宏。

[範本](../cpp/templates-cpp.md)<br/>
範本規格、函式樣板、類別樣板、 **`typename`** 關鍵字、範本與宏、範本和智慧型指標。

[事件處理](../cpp/event-handling.md)<br/>
宣告事件及事件處理常式。

[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)<br/>
Microsoft C++ 專有的修飾詞。 記憶體定址、呼叫慣例、 **`naked`** 函數、擴充的儲存類別屬性（ **`__declspec`** ）、 **`__w64`** 。

[內嵌組譯工具](../assembler/inline/inline-assembler.md)<br/>
在區塊中使用元件語言和 c + + **`__asm`** 。

[編譯器 COM 支援](../cpp/compiler-com-support.md)<br/>
Microsoft 專有類別和全域函式的參考，可用來支援 COM 類型。

[Microsoft 擴充功能](../cpp/microsoft-extensions.md)<br/>
Microsoft C++ 擴充功能。

[非標準行為](../cpp/nonstandard-behavior.md)<br/>
Microsoft c + + 編譯器非標準行為的相關資訊。

[歡迎回到 C++](welcome-back-to-cpp-modern-cpp.md)<br/>
概述撰寫安全、正確且有效率的程式的新式 c + + 程式設計實務。

## <a name="related-sections"></a>相關章節

[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)<br/>
有關使用 Microsoft c + + 編譯器以 .NET 為目標的參考資料。

[C/C++ 建置參考](../build/reference/c-cpp-building-reference.md)<br/>
編譯器選項、連結器選項和其他建置工具。

[C/c + + 預處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
有關 pragma、前置處理器指示詞、預先定義巨集和前置處理器的參考資料。

[Visual C++ 程式庫](../standard-library/cpp-standard-library-reference.md)<br/>
各種 Microsoft c + + 程式庫參考起始頁的連結清單。

## <a name="see-also"></a>另請參閱

[C 語言參考](../c-language/c-language-reference.md)
