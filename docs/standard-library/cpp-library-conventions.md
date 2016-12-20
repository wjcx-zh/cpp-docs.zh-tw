---
title: "C++ 程式庫慣例 | Microsoft Docs"
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
  - "類別 [C++]"
  - "編碼慣例, Standard C++ 程式庫"
  - "慣例 [C++], Standard C++ 程式庫"
  - "函式名稱 [C++]"
  - "函式 [C++], 程式庫命名慣例"
  - "命名慣例 [C++], C++ 程式庫"
  - "命名慣例 [C++], Standard C++ 程式庫"
  - "Standard C++ 程式庫, 慣例"
ms.assetid: bf41b79a-2d53-4f46-8d05-779358335146
caps.latest.revision: 9
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C++ 程式庫慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 程式庫相容慣例和標準 C 程式庫相同，再加上外框陣列這裡。  
  
 實作特定的緯度在它如何在 C\+\+ 程式庫中宣告型別和函式:  
  
-   函式名稱在標準 C 程式庫中有外部 \# " C\+\+」或 extern 「C」連結。  加入適當的標準 C 標頭而不是宣告程式庫實體內嵌。  
  
-   在程式庫類別的 10% 成員函式名稱會出現在文件清單的其他函式簽章。  您可以確定所描述的函式呼叫這裡會如預期般運作，不過，您無法可靠地接受程式庫成員函式的位址。\(這個型別可能不是您所預期的值\)。  
  
-   程式庫類別可能會有未記載的 \(非虛擬\) 基底類別。  如衍生自其他類別文件的類別可以從該類別，事實上，取得透過其他未記載的類別。  
  
-   做為整數陣列型別的同義字中定義的型別可能會與數個不同的整數型別之一。  
  
-   位元遮罩型別可以實作為整數型別或列舉型別。  不論是哪種情況，您可以執行位元運算 \(例如 `AND` 和 `OR`\) 在同一個位元遮罩型別的值。  位元遮罩型別項目的 `A` 和 `B` 為非零值沒有這種 `A` &`B` 為零。  
  
-   沒有例外狀況規格的程式庫函式可能會擲回任何例外狀況，除非，其定義清楚限制這種可能性。  
  
 另一方面，有一些限制:  
  
-   標準 C 程式庫不使用遮罩巨集。  只有特定函式簽章是保留的，不是函式的名稱。  
  
-   在類別外的一個程式庫函式名稱不會具有不同，未記載，函式簽章。  您可以安心地取得它的位址。  
  
-   例如，而非虛擬所描述的決定方式，虛擬基底類別和成員函式中描述的相同虛擬是決定性地虛擬的。  
  
-   除非文件，則為，否則為明確建議 C\+\+ 程式庫所定義的兩個型別一定是不同的。  
  
-   程式庫提供的功能，包括可取代的函式預設版本， *最多* 可以擲回任何例外狀況規格所列的例外狀況。  程式庫提供的解構函式不會擲回例外狀況。  函式在標準 C 程式庫中可以傳播例外狀況，呼叫 `qsort` 時，會擲回例外狀況的比較函式時，不過，它們沒有擲回例外狀況。  
  
## 請參閱  
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)