---
title: "多位元組字元和寬字元 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字元碼 [C++], 多位元組"
  - "字元碼 [C++], 寬"
  - "字元資料類型 [C]"
  - "字元 [C++], 程式碼"
  - "字元 [C++], 寬"
  - "全球化 [C++], 字元集"
  - "國際化應用程式 [C++], 字元顯示"
  - "多位元組字元 [C++]"
  - "類型 [C], 字元"
  - "Unicode [C++], 寬字元集"
  - "寬字元 [C++]"
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 多位元組字元和寬字元
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多位元組字元是由一個或多個位元組序列組成的字元。  每個位元組序列表示擴充字元集的單一字元。  多位元組字元用於如漢字等字元集。  
  
 寬字元是寬度永遠為 16 位元的多語系字元碼。  字元常數的類型為 `char`，若是寬字元，則其類型為 `wchar_t`。  因為寬字元永遠以固定的大小來表示，所以使用寬字元簡化了含國際化字元集的程式設計。  
  
 寬字元字串常值 `L"hello"` 會成為 6 個類型為 `wchar_t` 的整數陣列。  
  
```  
{L'h', L'e', L'l', L'l', L'o', 0}  
```  
  
 Unicode 規格是寬字元的規格。  要在多位元組和寬字元之間轉換的執行階段程式庫常式包括 `mbstowcs`、`mbtowc`、`wcstombs` 和 `wctomb`。  
  
## 請參閱  
 [C 識別項](../c-language/c-identifiers.md)