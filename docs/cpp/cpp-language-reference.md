---
title: "C++ 語言參考 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
f1_keywords: 
  - "c++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++, 語言參考"
  - "語言參考"
  - "語言參考, Visual C++"
  - "Visual C++, 語言參考"
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 語言參考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本參考資料將說明 Microsoft Visual C\+\+ 中實作的 C\+\+ 程式語言。  本參考資料是根據《*The Annotated C\+\+ Reference Manual*》\(標註的 C\+\+ 參考手冊，作者 Margaret Ellis 和 Bjarne Stroustrup\) 與 ANSI\/ISO C\+\+ 國際標準 \(ISO\/IEC FDIS 14882\) 編成。  已包含 Microsoft 專有 C\+\+ 語言功能實作。  
  
 請參閱下表，快速尋找關鍵字或運算子：  
  
-   [C\+\+ 關鍵字](../cpp/keywords-cpp.md)  
  
-   [C\+\+ 運算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
  
## 在本節中  
 [語彙慣例](../cpp/lexical-conventions.md)  
 C \+\+ 程式的基本語彙元素：語彙基元、註解、運算子、關鍵字、標點符號、常值。  另外還有檔案轉譯、運算子優先順序\/關聯性。  
  
 [基本概念](../cpp/basic-concepts-cpp.md)  
 範圍、連結、程式啟動和結束、儲存類別以及類型。  
  
 [標準轉換](../cpp/standard-conversions.md)  
 內建 \(或「基本」\) 類型之間的類型轉換。  另外還有算術轉換，以及指標、參考與成員指標類型之間的轉換。  
  
 [運算子、優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)  
 C\+\+ 中的運算子。  
  
 [運算式](../cpp/expressions-cpp.md)  
 運算式類型、運算式語意、運算子參考主題、轉型和轉型運算子、執行階段類型資訊。  
  
 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)  
 程式設計技巧，可隱含定義函式物件類別和建構該類別類型的函式物件。  
  
 [陳述式](../cpp/statements-cpp.md)  
 運算式、null、複合、選取、反覆項目、跳躍和宣告陳述式。  
  
 [宣告](../misc/declarations.md)  
 儲存類別指定名稱、函式定義、初始化、列舉、類別、結構以及等位宣告和 typedef 宣告。  另外還有內嵌函式、const 關鍵字和命名空間。  
  
 [宣告子](http://msdn.microsoft.com/zh-tw/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)  
 宣告陳述式中為物件、類型或函式命名的部分。  抽象宣告子、類型名稱、初始設定式、函式宣告與定義、陣列、參考。  
  
 [類別、結構和等位](../cpp/classes-and-structs-cpp.md)  
 類別、結構和等位簡介。  另外還有成員函式、資料成員、位元欄位、this 指標、巢狀類別。  
  
 [衍生類別](../cpp/inheritance-cpp.md)  
 單一和多重繼承、虛擬函式、多重基底類別、抽象類別、範圍規則。  另外還有 \_\_super 和 \_\_interface 關鍵字。  
  
 [成員存取控制](../cpp/member-access-control-cpp.md)  
 控制類別成員的存取：public、private 和 protected 關鍵字。  Friend 函式和類別。  
  
 [特殊成員函式](../misc/special-member-functions-cpp.md)  
 類別類型獨有的特殊函式：建構函式、解構函式、轉換函式、指派運算子、new 運算子和 delete 運算子函式。  
  
 [多載化](../misc/overloading-cpp.md)  
 多載函式、宣告比對、引數比對。  另外還有多載運算子、運算子多載規則。  
  
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)  
 C\+\+ 例外狀況處理、結構化例外狀況處理 \(SEH\)、用於撰寫例外狀況處理陳述式的關鍵字。  
  
 [判斷提示和使用者提供的訊息](../cpp/assertion-and-user-supplied-messages-cpp.md)  
 `#error` 指示詞、`static_assert` 關鍵字、`assert` 巨集。  
  
 [範本](../cpp/templates-cpp.md)  
 樣板規格、函式樣板、類別樣板、typename 關鍵字、樣板與  巨集、樣板和智慧型指標。  
  
 [事件處理](../cpp/event-handling.md)  
 宣告事件及事件處理常式。  
  
 [Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)  
 Microsoft C\+\+ 專有的修飾詞。  記憶體定址、呼叫慣例、naked 函式、擴充儲存類別屬性 \(\_\_declspec\)、\_\_w64。  
  
 [內嵌組合語言](../assembler/inline/inline-assembler.md)  
 在 \_\_asm 區塊中使用組合語言和 C\+\+。  
  
 [編譯器 COM 支援](../cpp/compiler-com-support.md)  
 Microsoft 專有類別和全域函式的參考，可用來支援 COM 類型。  
  
 [Microsoft 擴充功能](../cpp/microsoft-extensions.md)  
 Microsoft C\+\+ 擴充功能。  
  
 [非標準行為](../cpp/nonstandard-behavior.md)  
 有關 Visual C\+\+ 編譯器非標準行為的資訊。  
  
## 相關章節  
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)  
 有關使用 Visual C\+\+ 將通用語言執行平台設定為目標的參考資料。  
  
 [C\/C\+\+ 建置參考](../build/reference/c-cpp-building-reference.md)  
 編譯器選項、連結器選項和其他建置工具。  
  
 [C\/C\+\+ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)  
 有關 pragma、前置處理器指示詞、預先定義巨集和前置處理器的參考資料。  
  
 [Visual C\+\+ 程式庫](http://msdn.microsoft.com/zh-tw/fec23c40-10c0-4857-9cdc-33a3b99b30ae)  
 各種 Visual C\+\+ 程式庫之參考起始頁的連結清單。  
  
## 請參閱  
 [C 語言參考](../c-language/c-language-reference.md)