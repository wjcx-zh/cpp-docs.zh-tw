---
title: "模組定義陳述式的規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".def"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "模組定義檔"
  - "模組定義檔, 陳述式語法"
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 模組定義陳述式的規則
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列語法規則套用至 .def 檔中所有的陳述式。  其他套用至特定陳述式的規則，則隨著各陳述式說明。  
  
-   陳述式、屬性關鍵字和使用者指定的識別項都是有區分大小寫的。  
  
-   包含空格或分號 \(;\) 的長檔名必須以引號 \("\) 括住。  
  
-   使用一個或多個空格、定位字元或新行字元，來分隔陳述式關鍵字和其引數，以及分隔各陳述式。  指定引數的冒號 \(:\) 或等號 \(\=\) 會以零個或多個空格、定位字元或新行字元括住。  
  
-   如果使用 **NAME** 或 **LIBRARY** 陳述式，則這兩個陳述式必須在其他所有陳述式之前。  
  
-   **SECTIONS** 和 **EXPORTS** 陳述式可在 .def 檔中出現一次以上。  每一個陳述式都可接受多個規格，而規格必須以一個或多個空格、定位字元或新行字元分隔。  陳述式關鍵字必須在第一個規格之前出現一次，並可在每個其他規格之前重複。  
  
-   很多陳述式都有相等的 LINK 命令列選項。  如需詳細資訊，請參閱對應的 LINK 選項之說明。  
  
-   .def 檔中的註解是由各註解行開頭的分號 \(;\) 指定。  註解不可與陳述式共用一行，但可出現在多行陳述式中的規格之間 \(**SECTIONS** 和 **EXPORTS** 為多行陳述式\)。  
  
-   數值引數是以十進位或十六進位指定。  
  
-   如果字串引數與[保留字](../../build/reference/reserved-words.md)相符，則該字串必須以雙引號 \("\) 括住。  
  
## 請參閱  
 [模組定義檔案 \(.Def\)](../../build/reference/module-definition-dot-def-files.md)   
 [Frequently Asked Questions on Building](http://msdn.microsoft.com/zh-tw/56a3bb8f-0181-4989-bab4-a07ba950ab08)