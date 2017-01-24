---
title: "C++/CLI 移轉入門 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++/CLI 2 版"
  - "C++/CLI 2 版, Managed Extensions"
  - "Managed Extensions for C++, 升級語法"
  - "移轉 [C++], C++/CLI 2 版"
  - "升級 Visual C++ 應用程式, Managed Extensions for C++ 移至 Visual C++ 2005 語法"
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++/CLI 移轉入門
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本章節將引導您如何將 Visual C\+\+ 程式從 Managed Extensions for C\+\+ 移至 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)]。  如需語法變更的檢查清單摘要，請參閱 [\(NOTINBUILD\)Managed Extensions for C\+\+ Syntax Upgrade Checklist](http://msdn.microsoft.com/zh-tw/edbded88-7ef3-4757-bd9d-b8f48ac2aada)。  
  
 C\+\+\/CLI 將動態元件程式設計開發架構 \(Programming Paradigm\) 擴充成 ISO\-C\+\+ 標準語言。  新語言提供許多優於 Managed Extensions 的重大改進功能。  本章節提供 Managed Extensions for C\+\+ 語言功能的列舉清單，以及這些功能對 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 的對應 \(如果有的話\)，若沒有對應，則會指出它們的建構。  
  
## 本章節內容  
 [變更大綱 \(C\+\+\/CLI\)](../dotnet/outline-of-changes-cpp-cli.md)  
 快速參考的高層級大綱，提供分為五大類別的變更清單。  
  
 [語言關鍵字 \(C\+\+\/CLI\)](../dotnet/language-keywords-cpp-cli.md)  
 討論語言關鍵字的變更，包括雙底線的移除以及內容和含空格關鍵字的引入。  
  
 [Managed 類型 \(C\+\+\/CL\)](../dotnet/managed-types-cpp-cl.md)  
 說明 Common Type System \(CTS\) 宣告中的語法變更，包括了類別、陣列 \(包括參數陣列\)、列舉等宣告中的變更。  
  
 [在類別或介面中的成員宣告 \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 說明關於類別成員的變更，例如純量屬性、索引屬性、運算子、委派 \(Delegate\) 及事件。  
  
 [實值類型和行為 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 詳細說明實值型別 \(Value Type\) 以及新的內部指標和 Pin 指標系列，  也會討論一些重大的語意變更，例如隱含 Boxing 簡介、Boxed 實值型別的不變性以及數值類別中預設建構函式 \(Constructor\) 支援的移除。  
  
 [一般的語言變更](../dotnet/general-language-changes-cpp-cli.md)  
 詳細說明語意變更，例如轉換通知的支援、字串常值 \(String Literal\) 行為以及 ISO\-C\+\+ 和 C\+\+\/CLI 間的語意變更。  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Component Extensions for Runtime Platforms](../windows/component-extensions-for-runtime-platforms.md)