---
title: "malloc 對齊 | Microsoft Docs"
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
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# malloc 對齊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[malloc](../c-runtime-library/reference/malloc.md) 保證會傳回用來儲存任何已適當對齊之物件的記憶體，這個物件具有基本對齊，並且可容納於配置的記憶體數量中。  *基本對齊* 是小於或等於實作所支援的最大對齊 \(沒有對齊規格\)。\(在 Visual C\+\+ 中，這是針對 `double`或 8 位元組所需的對齊方式。  在以 64 位元平台為目標的程式碼中，這是 16 個位元組\)。例如，四個位元組的配置會在支援任何四個位元組或更小物件的界限上對齊。  
  
 Visual C\+\+ 允許有*擴充延伸對齊*的類型，也稱為*過度對齊*的類型。  例如，SSE 類型 [\_\_m128](../cpp/m128.md) 和 `__m256`，以及使用 `__declspec(align(``n``))` 宣告的類型 \(其中 `n` 大於 8\) 擁有延伸對齊。  `malloc` 不保證記憶體對齊在適合需要擴充對齊之物件的界限。  若要為過度對齊的類型配置記憶體，請使用 [\_aligned\_malloc](../c-runtime-library/reference/aligned-malloc.md) 和相關功能。  
  
## 請參閱  
 [堆疊使用方式](../build/stack-usage.md)   
 [align](../cpp/align-cpp.md)   
 [\_\_declspec](../cpp/declspec.md)