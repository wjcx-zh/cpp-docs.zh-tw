---
title: C++ 語言參考
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
ms.openlocfilehash: 69b244a1559a4570cc00a72d86426a7929ffc474
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469377"
---
# <a name="c-language-reference"></a>C++ 語言參考

本参考将介绍在 Microsoft Visual C++ 中实现的 C++ 编程语言。 于组织*C++ 参考手册批注 》* Margaret Ellis 和 Bjarne stroustrup 撰写和 ANSI/ISO C++ 国际标准 (ISO/IEC FDIS 14882)。 本文涵盖了 C++ 语言功能的 Microsoft 专用实现。 

有关现代 C++ 编程做法的概述，请参阅[欢迎回到 C++](welcome-back-to-cpp-modern-cpp.md)。

請參閱下表，快速尋找關鍵字或運算子：

- [C++ 关键字](../cpp/keywords-cpp.md)

- [C++ 運算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>本節內容

[語彙慣例](../cpp/lexical-conventions.md)<br/>
C ++ 程式的基本語彙元素：語彙基元、註解、運算子、關鍵字、標點符號、常值。 另外還有檔案轉譯、運算子優先順序/關聯性。

[基本概念](../cpp/basic-concepts-cpp.md)<br/>
範圍、連結、程式啟動和結束、儲存類別以及類型。

[標準轉換](../cpp/standard-conversions.md)<br/>
內建 (或「基本」) 類型之間的類型轉換。 另外還有算術轉換，以及指標、參考與成員指標類型之間的轉換。

[運算子、 優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
C++ 中的運算子。

[運算式](../cpp/expressions-cpp.md)<br/>
運算式類型、運算式語意、運算子參考主題、轉型和轉型運算子、執行階段類型資訊。

[Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)<br/>
程式設計技巧，可隱含定義函式物件類別和建構該類別類型的函式物件。

[陳述式](../cpp/statements-cpp.md)<br/>
運算式、null、複合、選取、反覆項目、跳躍和宣告陳述式。

[宣告和定義](declarations-and-definitions-cpp.md)<br/>
儲存類別規範、 函式定義、 初始化、 列舉型別**類別**，**結構**，並**union**宣告，和**typedef**宣告。 此外，**內嵌**函式**const**關鍵字、 命名空間。

[類別、 結構和等位](../cpp/classes-and-structs-cpp.md)<br/>
類別、結構和等位簡介。 此外，成員函式、 特殊成員函式中，資料成員，位元欄位，**這**指標、 巢狀的類別。

[在衍生的類別](../cpp/inheritance-cpp.md)<br/>
單一和多重繼承**虛擬**函式、 多個基底類別**抽象**類別、 範圍規則。 此外， **__super**並 **__interface**關鍵字。

[成員存取控制](../cpp/member-access-control-cpp.md)<br/>
控制對類別成員的存取：**公開金鑰**，**私人**，和**保護**關鍵字。 Friend 函式和類別。

[多載](operator-overloading.md)<br/>
多載的運算子，運算子多載規則。

[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)<br/>
C++ 例外狀況處理、結構化例外狀況處理 (SEH)、用於撰寫例外狀況處理陳述式的關鍵字。

[判斷提示和使用者提供的訊息](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error` 指示詞**static_assert**關鍵字，`assert`巨集。

[範本](../cpp/templates-cpp.md)<br/>
樣板規格、 函式樣板、 類別樣板**typename**關鍵字、 樣板與巨集、 樣板和智慧型指標。

[事件處理](../cpp/event-handling.md)<br/>
宣告事件及事件處理常式。

[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)<br/>
Microsoft C++ 專有的修飾詞。 記憶體定址、 呼叫慣例**naked**函數，擴充儲存類別屬性 (**__declspec**)， **__w64**。

[內嵌組合語言](../assembler/inline/inline-assembler.md)<br/>
使用組件的語言和 c + + **__asm**區塊。

[編譯器 COM 支援](../cpp/compiler-com-support.md)<br/>
Microsoft 專有類別和全域函式的參考，可用來支援 COM 類型。

[Microsoft 延伸模組](../cpp/microsoft-extensions.md)<br/>
Microsoft C++ 擴充功能。

[非標準行為](../cpp/nonstandard-behavior.md)<br/>
有關 Visual C++ 編譯器非標準行為的資訊。

[歡迎回到 C++](welcome-back-to-cpp-modern-cpp.md)<br/>
撰寫安全、 正確且有效率的程式，做法現代 c + + 程式設計的概觀。

## <a name="related-sections"></a>相關章節

[執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)<br/>
有關使用 Visual C++ 將通用語言執行平台設定為目標的參考資料。

[C/C++ 建置參考](../build/reference/c-cpp-building-reference.md)<br/>
編譯器選項、連結器選項和其他建置工具。

[C/C++ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
有關 pragma、前置處理器指示詞、預先定義巨集和前置處理器的參考資料。

[Visual C++ 程式庫](../standard-library/cpp-standard-library-reference.md)<br/>
各種 Visual C++ 程式庫之參考起始頁的連結清單。

## <a name="see-also"></a>另請參閱

[C 語言參考](../c-language/c-language-reference.md)