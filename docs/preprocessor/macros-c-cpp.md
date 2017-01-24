---
title: "巨集 (C/C++) | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "前置處理器"
  - "前置處理器, 巨集"
  - "Visual C++, 前置處理器巨集"
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 巨集 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

前置處理會展開下列位置的巨集：所有不是前置處理器指示詞的程式碼行 \(開頭不是以 **\#** 做為第一個非空白字元的程式碼行\)，以及在條件式編譯的過程中不會略過的某些指示詞部分。「條件式編譯」指示詞可讓您隱藏原始程式檔某些部分的編譯，方法是透過測試常數運算式或識別項，判斷在前置處理期間，哪些文字區塊會傳遞到編譯器上，以及哪些文字區塊會從原始程式檔中移除。  
  
 `#define` 指示詞通常用於讓有意義的識別項與常數、關鍵字和常用的陳述式或運算式產生關聯。  表示常數的識別項有時稱為「符號常數」或「資訊清單常數」。表示陳述式或運算式的識別項稱為「巨集」。這份前置處理器文件中只會使用「巨集」這個詞彙。  
  
 在程式的原始文字或某些其他前置處理器命令的引數中辨識出巨集名稱時，會將它視為對該巨集的呼叫。  巨集名稱會以巨集主體的複本取代。  如果巨集接受引數，巨集名稱後面的實際引數就會取代巨集主體中的正式參數。  以處理的本體複本取代巨集呼叫的程序稱為「展開」巨集呼叫。  
  
 實際上，巨集分成兩種類型。「類似物件」的巨集不接受引數，而「類似函式」的巨集可以定義為接受引數，如此它們的外觀和行為都會像是函式呼叫。  由於巨集不會產生實際函式呼叫，因此您有時可以用巨集取代函式呼叫，讓程式執行得更快 \(在 C\+\+ 中，內嵌函式通常是慣用方法\)。不過，如果您定義和使用巨集時不夠謹慎，巨集就可能會製造問題。  您可能需要在具有引數的巨集定義中使用括號，以保持運算式中的適當優先順序。  此外，巨集也可能無法正確處理具有副作用的運算式。  如需詳細資訊，請參閱 [\#define 指示詞](../preprocessor/hash-define-directive-c-cpp.md)中的 `getrandom` 範例。  
  
 一旦定義了巨集，就不能在未先移除原始定義之前，將它重新定義為不同的值。  不過，您可以用完全相同的定義重新定義巨集。  因此，相同定義可以重複出現在程式中。  
  
 \#**undef** 指示詞會移除巨集的定義。  一旦移除了定義，您就可以將巨集重新定義為不同的值。  [\#define 指示詞](../preprocessor/hash-define-directive-c-cpp.md)和 [\#undef 指示詞](../preprocessor/hash-undef-directive-c-cpp.md)中將分別討論 `#define` 和 `#undef` 指示詞。  
  
 如需詳細資訊，請參閱：  
  
-   [巨集和 C\+\+](../preprocessor/macros-and-cpp.md)  
  
-   [Variadic 巨集](../preprocessor/variadic-macros.md)  
  
-   [預先定義的巨集](../preprocessor/predefined-macros.md)  
  
## 請參閱  
 [C\/C\+\+ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)