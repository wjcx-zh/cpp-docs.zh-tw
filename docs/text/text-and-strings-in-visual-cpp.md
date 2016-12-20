---
title: "Visual C++ 中的文字和字串 | Microsoft Docs"
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
  - "ASCII 字元 [C++]"
  - "字元集 [C++]"
  - "字元集 [C++], 關於字元集"
  - "字元集 [C++], 非歐洲系"
  - "全球化 [C++]"
  - "全球化 [C++], 字元集"
  - "國際化應用程式 [C++], 關於國際性應用程式"
  - "日文字元 [C++]"
  - "漢字字元支援 [C++]"
  - "區域字元集 [C++]"
  - "當地語系化 [C++]"
  - "當地語系化 [C++], 字元集"
  - "MBCS [C++], 國際化程式設計"
  - "多重語言支援 [C++]"
  - "非歐洲字元 [C++]"
  - "可移植性 [C++]"
  - "可移植性 [C++], 字元集"
  - "程式設計 [C++], 國際化"
  - "轉譯程式碼 [C++]"
  - "轉譯 [C++], 字元集"
  - "Unicode [C++]"
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
caps.latest.revision: 12
caps.handback.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Visual C++ 中的文字和字串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

為國際化市場開發應用程式重要的一點是區域字元集 \(Character Set\) 的適當表示。  ASCII 字元集定義範圍 0x00 到 0x7F 的字元。  還有其他的字元集，主要是歐洲的，將字元定義在範圍 0x00 到 0x7F 之間，與 ASCII 字元集相同，並且也定義從 0x80 到 0xFF 的擴充字元集。  因此，8 位元的單一位元組字元集 \(Single\-Byte Character Set，SBCS\) 足夠表示 ASCII 字元集，以及許多歐洲語言的字元集。  然而，某些非歐洲字元集，例如日語漢字，包含比單一位元組編碼配置所能表示的字元還要多，因此需要多位元組字元集 \(MBCS\) 編碼。  
  
## 本章節內容  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)  
 討論 Unicode 和 MBCS 程式設計的 Visual C\+\+ 支援。  
  
 [Unicode 的支援](../text/support-for-unicode.md)  
 說明 Unicode 是一種可支援所有的字元集的規格 \(包括不能以單一位元組表示的字元集\)。  
  
 [多位元組字元集 \(MBCS\) 的支援](../text/support-for-multibyte-character-sets-mbcss.md)  
 討論多位元組字元集 \(MBCS\)，這是除了 Unicode 以外，另一種支援字元集 \(例如不能以單一位元組表示的日語和中文\) 的替代方法。  
  
 [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)  
 提供許多資料型別、常式和其他物件的 Microsoft 特定泛用文字對應。  
  
 [如何：在各種字串類型之間轉換](../text/how-to-convert-between-various-string-types.md)  
 示範如何將各種 Visual C\+\+ 字串型別轉換成其他字串。  
  
## 相關章節  
 [國際化](../c-runtime-library/internationalization.md)  
 討論 C 執行階段程式庫的國際化支援。  
  
 [國際化範例](http://msdn.microsoft.com/zh-tw/aa8d390c-cf4c-4dd8-9dea-74d81f93f2f8)  
 提供 Visual C\+\+ 國際化的示範範例。  
  
 [語言和國家\/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
 提供 C 執行階段程式庫中的語言和國家\/地區字串。