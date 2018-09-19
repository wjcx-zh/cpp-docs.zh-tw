---
title: C++ 语言参考 |Microsoft 文档
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 708db2b20cdbbe2e322075789f64433ff70612a2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025512"
---
# <a name="c-language-reference"></a>C++ 語言參考

本参考将介绍在 Microsoft Visual C++ 中实现的 C++ 编程语言。 于组织*C++ 参考手册批注 》* Margaret Ellis 和 Bjarne stroustrup 撰写和 ANSI/ISO C++ 国际标准 (ISO/IEC FDIS 14882)。 本文涵盖了 C++ 语言功能的 Microsoft 专用实现。 

有关现代 C++ 编程做法的概述，请参阅[欢迎回到 C++](welcome-back-to-cpp-modern-cpp.md)。

請參閱下表，快速尋找關鍵字或運算子：

- [C++ 关键字](../cpp/keywords-cpp.md)

- [C++ 運算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>本節內容

[語彙慣例](../cpp/lexical-conventions.md)c + + 程式的基本語彙元素： 語彙基元、 註解、 運算子、 關鍵字、 標點符號、 常值。 另外還有檔案轉譯、運算子優先順序/關聯性。

[基本概念](../cpp/basic-concepts-cpp.md)範圍、 連結、 程式啟動和終止、 儲存體類別和類型。

[標準轉換](../cpp/standard-conversions.md)類型內建功能，或 「 基本 」 的型別之間的轉換。 另外還有算術轉換，以及指標、參考與成員指標類型之間的轉換。

[運算子、 優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)c + + 中的運算子。

[運算式](../cpp/expressions-cpp.md)運算式、 運算式語意、 型別參考的運算子、 轉型和轉型運算子，執行階段類型資訊的主題。

[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)程式設計技巧，可隱含定義函式物件類別和建構該類別類型的函式物件。

[陳述式](../cpp/statements-cpp.md)運算式、 null、 複合、 選取、 反覆項目、 跳躍和宣告陳述式。

[宣告和定義](declarations-and-definitions-cpp.md)儲存類別規範、 函式定義、 初始化、 列舉型別**類別**，**結構**，和**union**宣告，並**typedef**宣告。 此外，**內嵌**函式**const**關鍵字、 命名空間。

[類別、 結構和等位](../cpp/classes-and-structs-cpp.md)介紹類別、 結構和等位。 此外，成員函式、 特殊成員函式中，資料成員，位元欄位，**這**指標、 巢狀的類別。

[衍生類別](../cpp/inheritance-cpp.md)單一和多重繼承，**虛擬**函式、 多個基底類別**抽象**類別、 範圍規則。 此外， **__super**並 **__interface**關鍵字。

[成員存取控制](../cpp/member-access-control-cpp.md)控制對類別成員的存取：**公用**，**私人**，和**保護**關鍵字。 Friend 函式和類別。

[多載](operator-overloading.md)多載運算子、 運算子多載規則。

[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)c + + 例外狀況處理、 結構化例外狀況處理 (SEH)、 用於撰寫例外狀況處理陳述式的關鍵字。

[判斷提示和 User-Supplied 訊息](../cpp/assertion-and-user-supplied-messages-cpp.md)
 `#error`指示詞，但**static_assert**關鍵字`assert`巨集。

[範本](../cpp/templates-cpp.md)樣板規格、 函式樣板、 類別樣板**typename**關鍵字、 樣板與巨集、 樣板和智慧型指標。

[事件處理](../cpp/event-handling.md)宣告事件和事件處理常式。

[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)Microsoft c + + 專有的修飾詞。 記憶體定址、 呼叫慣例**naked**函數，擴充儲存類別屬性 (**__declspec**)， **__w64**。

[內嵌組合語言](../assembler/inline/inline-assembler.md)使用組合語言和 c + + **__asm**區塊。

[編譯器 COM 支援](../cpp/compiler-com-support.md)Microsoft 專有類別和全域函式，用來支援 COM 類型的參考。

[Microsoft 擴充功能](../cpp/microsoft-extensions.md)c + + 的 Microsoft 擴充功能。

[非標準行為](../cpp/nonstandard-behavior.md)Visual c + + 編譯器非標準行為的相關資訊。

[欢迎回到 C++](welcome-back-to-cpp-modern-cpp.md)用于编写安全、 正确且高效程序做法现代 C++ 编程的概述。

## <a name="related-sections"></a>相關章節

[執行階段平台的元件擴充功能](../windows/component-extensions-for-runtime-platforms.md)參考上使用 Visual c + + 以通用語言執行平台為目標的資料。

[C/c + + 建置參考](../build/reference/c-cpp-building-reference.md)編譯器選項、 連結器選項，以及其他建置工具。

[C/c + + 前置處理器參考 》](../preprocessor/c-cpp-preprocessor-reference.md)參考 pragma、 前置處理器指示詞、 預先定義的巨集和前置處理器上的資料。

[Visual c + + 程式庫](../standard-library/cpp-standard-library-reference.md)一份參考連結起始頁的各種 Visual c + + 程式庫。

## <a name="see-also"></a>另請參閱

[C 語言參考](../c-language/c-language-reference.md)