---
title: "使用 wmain 取代 main | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "wmain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "main 函式, 和 wmain 比較"
  - "wmain 函式"
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 wmain 取代 main
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 在 Unicode 程式設計模型中，您可以定義寬字元版本的 **main** 函式。  如果您要撰寫遵守 Unicode 規格的可攜式程式碼，請使用 **wmain** 而非 **main**。  
  
 您可以使用類似於 **main** 的格式將形式參數宣告為 **wmain**。  然後您可以傳遞寬字元引數以及 \(選擇性的\) 一個指向程式的寬字元環境指標。  **wmain** 的 `argv` 和 `envp` 參數都是 `wchar_t*` 型別。  
  
 如果您的程式使用 **main** 函式，則作業系統會在程式啟動時建立多位元組字元環境。  只有在需要時才會建立該環境的寬字元複本 \(例如，藉由呼叫 [\_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) 或 [\_wputenv](../c-runtime-library/reference/putenv-wputenv.md) 函式\)。  在第一次呼叫 `_wputenv` 時，或在第一次呼叫 `_wgetenv` 時，如果 MBCS 環境已經存在，則會建立對應的寬字元字串環境，然後再由 `_wenviron` 全域變數 \(是 `_environ` 全域變數的寬字元版本\) 指向該變數。  此時會同時存在兩個環境 \(MBCS 和 Unicode\) 的複本，並由作業系統在整個程式存留期裡進行維護。  
  
 同樣的，如果您的程式使用 **wmain** 函式，則會在第一次呼叫 `_putenv` 或 `getenv` 時建立 MBCS \(ASCII\) 環境，並透過 `_environ` 全域變數指向該環境。  
  
 如需有關 MBCS 環境的詳細資訊，請參閱《執行階段程式庫參考》中的[單一位元組和多位元組字元集](../c-runtime-library/single-byte-and-multibyte-character-sets.md)。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)