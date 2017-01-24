---
title: "Unicode：寬字元集 | Microsoft Docs"
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
  - "c.international"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "Unicode [C++], 寬字元集"
  - "寬字元 [C++], Unicode"
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Unicode：寬字元集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

寬字元是兩個位元組雙語字元碼。  任何全球現代計算環境中所使用的字元，包括各種技術符號和特殊印刷字元在內，都可以根據 Unicode 規格，以寬字元來表示。  開發和維護包括 Microsoft 的大型 Consortium， Unicode 標準多現在接受。  
  
 寬字元是 `wchar_t`型別。  寬字元字串是以 `wchar_t[]`陣列來作表示，並且以`wchar_t*` 指標指著。  您可以用任何 ASCII 字元，可藉由在字元前面加上字母`L`，用寬字元表示。  例如，L'\\0' 是終止的寬 \(16 位元\) `NULL` 字元。  同樣的，任何 ASCII 字串常值可以寬字元字串常值來作表示，藉由在 ASCII 常值的前面加上字母 L \(L"Hello"\)。  
  
 一般來說，寬字元需要的記憶體空間要比多位元組字元多，但處理較快。  除此之外，在多位元組編碼裡一次只能表示一個地區設定，然而全世界所有的字元集都可以同時用 Unicode 表示。  
  
## 請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)