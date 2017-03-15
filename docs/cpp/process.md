---
title: "處理序 | Microsoft Docs"
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
  - "Process"
  - "process_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], 處理序"
  - "process __declspec 關鍵字"
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 處理序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定您的 Managed 應用程式處理序應該使用特定全域變數的單一複本、靜態成員變數，或在處理序中的所有應用程式定義域中共用的靜態區域變數。  這主要是在以 **\/clr:pure** 進行編譯時使用，因為在 **\/clr:pure** 之下，全域和靜態變數預設是以每個應用程式定義域為基準。  在以 **\/clr** 進行編譯時，全域和靜態變數預設是以每個處理序為基準 \(不需要使用 `__declspec(process)`\)。  
  
 只有原生類型的全域變數、靜態成員變數或靜態區域變數可以使用 `__declspec(process)` 來標記。  
  
 在以 **\/clr:pure** 進行編譯時，標記為以每個處理序為基準的變數也必須宣告為 `const`。  這可確保每個處理序的變數在某個應用程式定義域中不會遭到變更，也不會在其他應用程式定義域中產生未預期的結果。  `__declspec(process)` 的主要用途是要在 **\/clr:pure** 下啟用全域變數、靜態成員變數或靜態區域變數的編譯時期初始化。  
  
 `process`  只有在使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 或 **\/clr:pure** 進行編譯時有效，使用 **\/clr:safe** 進行編譯時則無效。  
  
 如果您想要讓每一個應用程式定義域擁有自己的全域變數複本，請使用 [appdomain](../cpp/appdomain.md)。  
  
 如需詳細資訊，請參閱[應用程式定義域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)。  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)