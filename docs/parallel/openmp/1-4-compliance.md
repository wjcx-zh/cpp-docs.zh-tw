---
title: "1.4 符合標準 | Microsoft Docs"
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
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1.4 符合標準
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OpenMP C/c + + API 的實作是 *OpenMP 相容* 如果就會辨識並章節 1、 2、 3、 4 中所保留的所有項目，此規格，語意，而且僅供資訊，而且不屬於規格的附錄 c 附錄 A、 B、 D、 E 和 F。 無法 OpenMP 相容的實作，包括 API 的子集。  
  
 OpenMP C 和 c + + API 是基底實作所支援的語言擴充功能。 如果基底的語言不支援的語言建構或延伸模組，會出現此文件中，OpenMP 實作不會需要來支援它。  
  
 所有標準的 C 和 c + + 程式庫函式和內建函式 （也就是編譯器對於這個特定的函數） 必須是安全執行緒。 未同步處理的使用平行區域內的不同執行緒的安全執行緒 – 函式不會產生未定義的行為。 不過，行為可能無法與序列的區域相同。 （隨機號碼產生函式是一個範例）。  
  
 OpenMP C/c + + API 可讓您指定的特定行為 *實作定義。* 合格的 OpenMP 實作，才能夠定義和文件在這些情況下其行為。 請參閱 [附錄 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md), ，頁面上 97，實作定義行為的清單。