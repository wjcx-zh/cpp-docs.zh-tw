---
title: "單位元組和多位元組字元集 | Microsoft Docs"
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
  - "c.character.multibyte"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "字元集 [C++], 多位元組"
  - "字元集 [C++], 單一位元組"
  - "MBCS [C++], 關於 MBCS"
  - "SBCS (單一位元組字元集)"
ms.assetid: 2cbc78ea-33c0-4cfb-b0df-7ce2458431ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 單位元組和多位元組字元集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ASCII 字元集定義範圍 0x00 到 0x7F 的字元。  還有許多其他的字元集，主要是歐洲的，將字元定義在範圍 0x00 到 0x7F 之間，與 ASCII 字元集相同，並且也定義從 0x80 到 0xFF 的擴充字元集。  因此，8 位元的單一位元組字元集 \(`SBCS`\) 足夠表示 ASCII 字元集，以及許多歐洲語言的字元集。  然而，某些非歐洲字元集，例如日語漢字，包含比單一位元組編碼配置所能表示的字元還要多，因此需要多位元組字元集 \(`MBCS`\) 編碼。  
  
> [!NOTE]
>  許多Microsoft 執行階段程式庫中的 `SBCS` 常式適當地處理多位元組、字元和字串。  許多多位元組字元集定義 ASCII 字元集為子集。  在許多多位元組字元集中，範圍 0x00 – 0x7F 內的每一字元與 ASCII 字元集裡有同樣值的字元完全相同。  例如，在 `ASCII` 和 `MBCS` 字元字串中，1 位元 `NULL` 字元 \('\\0'\) 的值是 0x00，並且表示終止的 null 字元。  
  
 多位元組字元集可能包含位元組和雙位元組字元。  因此多位元組字元字串可能包含單一位元組和雙位元組字元組合。  一位數的多位元組字元的前導位元組和後隨位元組。  在特殊的多位元組字元集裡，前導位元組落在某些範圍，後隨位元組也一樣。  當這些範圍重疊時，可能需要評估特定內容，以決定給定位元組是做為前導位元組還是後隨位元組。  
  
## 請參閱  
 [國際化](../c-runtime-library/internationalization.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)