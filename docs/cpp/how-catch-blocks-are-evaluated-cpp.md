---
title: "評估 Catch 區塊的方式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ 例外狀況處理, catch 處理常式"
  - "catch 關鍵字 [C++], catch 處理常式的類型"
  - "例外狀況處理, 攔截及刪除例外狀況"
  - "try-catch 關鍵字 [C++], 可攔截的類型"
  - "類型 [C++], 例外狀況處理"
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 評估 Catch 區塊的方式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 可讓您擲回任何類型的例外狀況，不過，一般建議擲回衍生自 std::exception 的類型。  C\+\+ 例外狀況可由指定與擲回例外狀況相同類型的 **catch** 處理常式加以攔截，或是由可攔截任何例外狀況類型的處理常式加以攔截。  
  
 如果擲回的例外狀況類型是類別，而該類別同時擁有一個或多個基底類別，則可以使用接受例外狀況類型的基底類別，以及接受例外狀況類型之基底參考的處理常式攔截例外狀況。  請注意，如果是以參考攔截例外狀況，它會繫結至實際擲回的例外狀況物件，否則它會是複本 \(就如同函式的引數\)。  
  
 擲回例外狀況時，它可能是由下列類型的 **catch** 處理常式所攔截：  
  
-   可以接受任何類型的處理常式 \(使用省略語法\)。  
  
-   可以接受與例外狀況物件相同類型的處理常式。由於它是複本，因此會忽略 **const**和 `volatile` 修飾詞。  
  
-   可以接受與例外狀況物件相同類型之參考的處理常式。  
  
-   可以接受與例外狀況物件相同類型的 **const** 或 `volatile` 形式之參考的處理常式。  
  
-   可以接受與例外狀況物件相同類型之基底類別的處理常式。由於它是複本，因此會忽略 **const** 和 `volatile` 修飾詞。  基底類別的 **catch** 處理常式不得放在衍生類別的 **catch** 處理常式前面。  
  
-   可以接受與例外狀況物件相同類型的基底類別之參考的處理常式。  
  
-   可以接受與例外狀況物件相同類型的基底類別之 **const** 或 `volatile` 形式參考的處理常式。  
  
-   可以接受指標的處理常式，擲回的指標物件可以透過標準指標轉換規則轉換成該指標。  
  
 **catch** 處理常式出現的順序很重要，因為指定之 **try** 區塊的處理常式是依照其出現的順序進行檢查。  例如，將基底類別的處理常式放在衍生類別的處理常式前面就是錯誤的範例。  找到相符的 **catch** 處理常式之後，就不會檢查後續處理常式。  因此，省略 **catch** 處理常式必須是其 **try** 區塊中的最後一個處理常式。  例如：  
  
```  
// ...  
try  
{  
    // ...  
}  
catch( ... )  
{  
    // Handle exception here.  
}  
// Error: the next two handlers are never examined.  
catch( const char * str )  
{  
    cout << "Caught exception: " << str << endl;  
}  
catch( CExcptClass E )  
{  
    // Handle CExcptClass exception here.  
}  
```  
  
 在這個範例中，省略 **catch** 處理常式是唯一會進行檢查的處理常式。  
  
## 請參閱  
 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)