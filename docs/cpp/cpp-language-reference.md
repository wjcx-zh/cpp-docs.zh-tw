---
title: C + + 語言參考 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 852f4522ecf32643611f6bbd4d86028e883bb6eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-language-reference"></a>C++ 語言參考
本參考資料將說明 Microsoft Visual C++ 中實作的 C++ 程式語言。 組織根據*標註 c + + 參考手冊*作者 Margaret Ellis 和 Bjarne Stroustrup 與 ANSI/ISO c + + 國際標準 (ISO/IEC FDIS 14882)。 已包含 Microsoft 專有 C++ 語言功能實作。  

如需現代 c + + 程式設計做法的概觀，請參閱[歡迎回到 c + +](welcome-back-to-cpp-modern-cpp.md)。
  
 請參閱下表，快速尋找關鍵字或運算子：  
  
-   [C + + 關鍵字](../cpp/keywords-cpp.md)  
  
-   [C++ 運算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  
## <a name="in-this-section"></a>本節內容  

 [語彙慣例](../cpp/lexical-conventions.md)  
 C ++ 程式的基本語彙元素：語彙基元、註解、運算子、關鍵字、標點符號、常值。 另外還有檔案轉譯、運算子優先順序/關聯性。  
  
 [基本概念](../cpp/basic-concepts-cpp.md)  
 範圍、連結、程式啟動和結束、儲存類別以及類型。  
  
 [標準轉換](../cpp/standard-conversions.md)  
 內建 (或「基本」) 類型之間的類型轉換。 另外還有算術轉換，以及指標、參考與成員指標類型之間的轉換。  
  
 [運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 C++ 中的運算子。  
  
 [運算式](../cpp/expressions-cpp.md)  
 運算式類型、運算式語意、運算子參考主題、轉型和轉型運算子、執行階段類型資訊。  
  
 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)  
 程式設計技巧，可隱含定義函式物件類別和建構該類別類型的函式物件。  
  
 [陳述式](../cpp/statements-cpp.md)  
 運算式、null、複合、選取、反覆項目、跳躍和宣告陳述式。  
  
 [宣告和定義](declarations-and-definitions-cpp.md)  
 儲存類別指定名稱、函式定義、初始化、列舉、類別、結構以及等位宣告和 typedef 宣告。 另外還有內嵌函式、const 關鍵字和命名空間。  
  
 [宣告子](http://msdn.microsoft.com/en-us/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)  
 宣告陳述式中為物件、類型或函式命名的部分。 抽象宣告子、類型名稱、初始設定式、函式宣告與定義、陣列、參考。  
  
 [類別、 結構和等位](../cpp/classes-and-structs-cpp.md)  
 類別、結構和等位簡介。 此外，成員函式、 特殊成員函式、 資料成員、 位元欄位、 this 指標、 巢狀的類別。  
  
 [在衍生的類別](../cpp/inheritance-cpp.md)  
 單一和多重繼承、虛擬函式、多重基底類別、抽象類別、範圍規則。 此外，__super 和\__interface 關鍵字。  
  
 [成員存取控制](../cpp/member-access-control-cpp.md)  
 控制類別成員的存取：public、private 和 protected 關鍵字。 Friend 函式和類別。  
  
 [多載化](operator-overloading.md)  
 多載的運算子時，多載運算子的規則。  
  
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)  
 C++ 例外狀況處理、結構化例外狀況處理 (SEH)、用於撰寫例外狀況處理陳述式的關鍵字。  
  
 [判斷提示和使用者提供的訊息](../cpp/assertion-and-user-supplied-messages-cpp.md)  
 `#error` 指示詞、`static_assert` 關鍵字、`assert` 巨集。  
  
 [範本](../cpp/templates-cpp.md)  
 樣板規格、函式樣板、類別樣板、typename 關鍵字、樣板與巨集、樣板和智慧型指標。  
  
 [事件處理](../cpp/event-handling.md)  
 宣告事件及事件處理常式。  
  
 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)  
 Microsoft C++ 專有的修飾詞。 記憶體定址、 呼叫慣例、 naked 函式、 擴充儲存類別屬性 (__declspec)、 \__w64。  
  
 [內嵌組合語言](../assembler/inline/inline-assembler.md)  
 在 __asm 區塊中使用組合語言和 C++。  
  
 [編譯器 COM 支援](../cpp/compiler-com-support.md)  
 Microsoft 專有類別和全域函式的參考，可用來支援 COM 類型。  
  
 [Microsoft 延伸模組](../cpp/microsoft-extensions.md)  
 Microsoft C++ 擴充功能。  
  
 [非標準行為](../cpp/nonstandard-behavior.md)  
 有關 Visual C++ 編譯器非標準行為的資訊。  

 [歡迎回到 c + +](welcome-back-to-cpp-modern-cpp.md)概觀現代 c + + 程式設計做法撰寫安全、 正確且有效率的程式。
  
## <a name="related-sections"></a>相關章節  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)  
 有關使用 Visual C++ 將通用語言執行平台設定為目標的參考資料。  
  
 [C/C++ 建置參考](../build/reference/c-cpp-building-reference.md)  
 編譯器選項、連結器選項和其他建置工具。  
  
 [C/C++ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)  
 有關 pragma、前置處理器指示詞、預先定義巨集和前置處理器的參考資料。  
  
 [Visual C++ 程式庫](../standard-library/cpp-standard-library-reference.md)  
 各種 Visual C++ 程式庫之參考起始頁的連結清單。  
  
## <a name="see-also"></a>請參閱  
 [C 語言參考](../c-language/c-language-reference.md)