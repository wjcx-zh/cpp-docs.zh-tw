---
title: "wmain 使用的支援 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "wWinMain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "寬字元 [C++], wmain 函式"
  - "wmain 函式"
  - "wWinMain 函式"
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# wmain 使用的支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 支援定義 **wmain** 函式和傳遞寬字元引數到您的 Unicode 應用程式。  您將正式參數宣告為 **wmain**，使用類似於 **main** 的格式。  然後您可以傳遞寬字元引數以及 \(選擇性的\) 一個指向程式的寬字元環境指標。  **wmain** 的 `argv` 和 `envp` 參數都是 `wchar_t*` 型別。  例如：  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  MFC Unicode 應用程式使用 **wWinMain** 來當做進入點 \(Entry Point\)。  在這個例子裡，`CWinApp::m_lpCmdLine` 是 Unicode 字串。  請務必用 [\/ENTRY](../build/reference/entry-entry-point-symbol.md) 連結器 \(Linker\) 選項來設定 **wWinMainCRTStartup**。  
  
 如果您的程式使用 **main** 函式，則多位元組字元環境就會在程式啟動時由 Run\-Time 程式庫建立。  環境的寬字元複本只有在需要時才建立 \(例如，藉著呼叫 `_wgetenv` 或 `_wputenv` 函式\)。  第一次呼叫 `_wputenv`，或者如果 MBCS 環境已經存在，則在第一次呼叫 `_wgetenv` 時，會建立對應的寬字元字串環境。  接著環境由 `_wenviron` 全域變數指出，此為 `_environ` 全域變數的寬字元版本。  此時，會同時存在兩個環境 \(MBCS 和 Unicode\) 複本，並由整個程式存留期裡的執行階段系統進行維護。  
  
 同樣的，如果您的程式使用 **wmain** 函式，寬字元環境在程式啟動時建立，並且由 `_wenviron` 全域變數指著。  MBCS \(ASCII\) 環境是在第一次呼叫 `_putenv` 或 `getenv` 時建立，並且是由 `_environ` 全域變數所指向。  
  
## 請參閱  
 [Unicode 的支援](../text/support-for-unicode.md)   
 [Unicode 程式設計摘要](../text/unicode-programming-summary.md)   
 [WinMain 函式](http://msdn.microsoft.com/library/windows/desktop/ms633559)