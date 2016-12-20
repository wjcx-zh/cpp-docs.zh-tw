---
title: "Basic Mechanics of Attributes | Microsoft Docs"
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
  - "attributes [C++], inserting in code"
  - "attributes [C++], about attributes"
ms.assetid: dc2069c3-b9f3-4a72-965c-4e5208ce8e34
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Basic Mechanics of Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有三種方法可將插入專案的屬性。  首先，您可以將這些手動插入您的程式碼。  其次，您可以插入專案中使用屬性方格的物件。  最後，您可以將它們使用不同的精靈。  如需有關如何使用 \[屬性\] 視窗中的色彩和各種精靈的詳細資訊，請參閱[建立和管理 Visual C\+\+ 專案](../ide/creating-and-managing-visual-cpp-projects.md)。  
  
 開始使用 Visual C\+\+。NET 中，編譯器可以辨識的原始程式檔中的屬性存在，而且可以動態地剖析和編譯時將進行驗證。  
  
 為前，專案建置時，編譯器剖析產生目的檔每個 C\+\+ 原始程式檔。  不過，當編譯器遇到一個屬性，它會在語法上驗證。  編譯器接著會動態呼叫屬性提供者來插入程式碼，或在編譯時期進行其他修改。  屬性的型別而定，不同的提供者實作。  例如，ATL 相關的屬性是由 Atlprov.dll 的方式實作。  
  
 下圖示範編譯器和屬性提供者之間的關係。  
  
 ![元件屬性通訊](../windows/media/vccompattrcomm.png "vcCompAttrComm")  
  
> [!NOTE]
>  屬性使用方式並不會改變原始程式檔的內容。  在偵錯工作階段期間，是唯一的時候，產生的屬性程式碼會顯示。  此外，專案中每個原始程式檔，您可以產生一個文字檔，就會顯示屬性替換結果。  如需有關此程序的詳細資訊，請參閱 [\/fx 將加入 \(合併插入程式碼\)](../build/reference/fx-merge-injected-code.md) 和[偵錯插入程式碼](../Topic/How%20to:%20Debug%20Injected%20Code.md)。  
  
 就像大部分的 C\+\+ 建構，屬性會有一組特性，定義適當的使用。  這就是屬性的內容，並且處理屬性的內容表，為每個屬性的參考主題。  例如，  [coclass](../windows/coclass.md) 屬性只會套用至現有類別或結構，而不是 [cpp\_quote](../windows/cpp-quote.md) 屬性，可以在 C\+\+ 原始程式檔的任何地方插入。  
  
## 請參閱  
 [Concepts](../windows/attributed-programming-concepts.md)