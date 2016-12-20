---
title: "main 函式和程式執行 | Microsoft Docs"
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
  - "進入點, 程式"
  - "main 函式"
  - "main 函式, 程式執行"
  - "程式啟動 [C++]"
  - "程式 [C++], 終止"
  - "啟始程式碼, main 函式"
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# main 函式和程式執行
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個 C 程式都必須有一個命名為 **main** 的主要 \(main\) 函式。  如果您的程式碼遵守 Unicode 程式設計模型，則可以使用寬字元版本的 **main**，即 **wmain**。  **main** 函式為程式執行的起點。  它通常會透過直接呼叫程式中的其他函式，以控制程式的執行。  程式通常會在 **main** 的結尾處停止執行，不過，它可能會因為各種理由而在程式的其他位置終止。  通常，在偵測到某個錯誤時，您可能會想要強制終止程式。  若要這麼做，請使用 **exit** 函式。  如需詳細資訊及使用 [exit](../c-runtime-library/reference/exit-exit-exit.md) 函式的範例，請參閱《執行階段程式庫參考》。  
  
## 語法  
  
```  
main( int argc, char *argv[ ], char *envp[ ] )  
```  
  
## 備註  
 原始程式中的函式會執行一個或多個特定工作。  **main** 函式可以呼叫這些函式來執行其各自的工作。  當 **main** 呼叫另一個函式時，它會將執行控制權傳遞給函式，因此，會從函式的第一個陳述式開始執行。  函式會在執行 `return` 陳述式到達函式結尾時，將控制權傳回 **main**。  
  
 您可以宣告任何函式，包括讓 **main** 具有參數。  詞彙「參數」或「型式參數」是指接收傳遞給函式之值的識別項。  如需將引數傳遞給參數的詳細資訊，請參閱[參數](../c-language/parameters.md)。  當某個函式呼叫另一個函式時，被呼叫的函式會從呼叫函式收到其參數的值。  這些值稱為「引數」。您可以對 **main** 宣告型式參數，使其可以使用此格式接收來自命令列的引數：  
  
 當您想要傳遞資訊給 **main** 函式時，這些參數通常會以傳統方式命名為 `argc` 和 `argv`，不過，C 編譯器不需要這些名稱。  `argc` 和 `argv` 的類型是由 C 語言所定義。  傳統上，如果有第三個參數要傳遞至 **main**，則該參數會命名為 `envp`。  本節稍後的範例將說明如何使用這三個參數存取命令列引數。  下列各節會說明這些參數。  
  
 如需寬字元版本 **main** 的說明，請參閱[使用 wmain](../c-language/using-wmain.md)。  
  
## 請參閱  
 [main：程式啟動](../cpp/main-program-startup.md)