---
title: "包含有括號的檔案名稱 | Microsoft Docs"
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
  - "C"
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 包含有括號的檔案名稱
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.8.2**：尋找可包含原始程式檔的方法  
  
 對於以角括弧括住的檔案規格，前置處理器不會搜尋父檔案的目錄。  「父」檔案是其中具有 [\#include](../preprocessor/hash-include-directive-c-cpp.md) 指示詞的檔案。  相反地，它會開始搜尋在編譯器命令列上 \/I 後方指定之目錄中的檔案。  如果 \/I 選項不存在或失敗，前置處理器會使用 INCLUDE 環境變數，在角括號內尋找任何 Include 檔。  INCLUDE 環境變數可以包含多個以分號 \(**;**\) 分隔的路徑。  如果多個目錄出現在 \/I 選項中或在 INCLUDE 環境變數中，前置處理器會以其出現的順序搜尋它們。  
  
## 請參閱  
 [前置處理指示詞](../c-language/preprocessing-directives.md)