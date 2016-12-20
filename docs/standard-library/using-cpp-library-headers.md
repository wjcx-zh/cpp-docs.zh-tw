---
title: "使用 C++ 程式庫標頭 | Microsoft Docs"
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
  - "頁首"
  - "頁首, 以 C++ include 指示詞命名"
  - "頁首, Standard C++ 程式庫"
  - "INCLUDE 指示詞"
  - "程式庫標頭"
  - "Standard C++ 程式庫, 頁首"
  - "C++ 的標準標頭"
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 C++ 程式庫標頭
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以將它命名為包含標準標頭的內容在包含指示詞。  
  
```  
#include <iostream>   // include I/O facilities  
```  
  
 您可以依任何順序、標準標頭，或定義相同巨集或相同型別的兩個或更多個標準標頭中包含標準標頭。  請不要在宣告中使用標準標頭。  不要定義同名關鍵字的巨集，在包含標準標頭之前。  
  
 C \+\+. 它需要定義需要的型別程式庫標頭包含任何其他 C\+\+ 程式庫標頭。\(永遠包含，然而，所有 C\+\+ 程式庫標頭在轉譯單位中明確需要，您唯恐錯誤猜測相對於其實際相依性\)。標準 C 標頭絕不包含其他標準標頭。  標準標頭宣告或定義為其描述的實體在文件。  
  
 每個函式位於程式庫在標準標頭宣告。  不同於在標準的 C 中，標準標頭從尚未提供遮罩巨集名稱和遮罩函式宣告並達到相同效果的函式相同。  如需遮罩巨集的詳細資訊，請參閱 [C\+\+ 程式庫慣例](../standard-library/cpp-library-conventions.md)。  
  
 除了 `operator delete` 和 `operator new` 之外的所有名稱在 C\+\+ 程式庫標頭會定義在 `std` 命名空間，或在 `std` 命名空間內形成巢狀的命名空間。  您參考的 `cin`，例如，做為 `std::cin`。  請注意，然而，巨集名稱不受命名空間限定性條件限制，因此，您一定要寫入的 `__STD_COMPLEX` ，而不用命名空間限定詞。  
  
 在一些轉譯環境，包括 C \+\+. 程式庫標頭可以提取之 `std` 命名空間中宣告的外部名稱將全域命名空間，與每一個別 `using` 宣告名稱。  否則，標題不會引入任何程式庫名稱到目前的命名空間。  
  
 C\+\+ 標準要求 C 標準標頭宣告在 `std`命名空間的所有外部名稱，然後提取至與個別 `using` 宣告的全域命名空間中每個的名稱。  但是，在某些轉譯環境 C 標準標頭不包含命名空間宣告，宣告所有的直接在全域命名空間。  因此，最可攜式方式涉及命名空間將遵循兩條規則:  
  
-   例如\>，的外部名稱，決定性地宣告在 `std` 命名空間中 \<stdlib.h 傳統上宣告包含標題 cstdlib \<。\>  知道名稱在全域命名空間也可能宣告。  
  
-   判斷區域宣告在全域命名空間中 \<stdlib.h 宣告的外部名稱，請\>直接包含標題 stdlib.h\>  \<。  知道命名空間 `std`也可能宣告。  
  
 因此，因此，如果您要呼叫 `std::abort` 會導致異常終止，應該包含 \<cstdlib\>。  如果您要呼叫 `abort`，您應包含 stdlib.h \<。\>  
  
 或者，您可以撰寫宣告:  
  
```  
using namespace std;  
```  
  
 要使所有程式庫名稱輸入目前命名空間。  如果您要立即寫入這個宣告，在所有包含指示詞後，您提取名稱將全域命名空間。  您可以接著忽略在這個轉譯單位中的其餘部分的命名空間的考量。  您也可以避免跨不同轉譯環境的大多數差異。  
  
 除非另外特別指出，您可能定義在 `std` 命名空間，或在 `std` 命名空間內形成巢狀的命名空間，在您的程式中。  
  
## 請參閱  
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)