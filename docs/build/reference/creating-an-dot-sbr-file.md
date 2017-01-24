---
title: "建立 .Sbr 檔 | Microsoft Docs"
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
  - ".sbr 檔案"
  - "BSCMAKE, 輸入檔"
  - "瀏覽資訊中的區域符號"
  - "SBR 檔案"
  - "來源瀏覽檔"
  - "符號"
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建立 .Sbr 檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BSCMAKE 的輸入檔是 .sbr 檔。  編譯器會為所編譯的每一個目的檔 \(.obj\) 建立一個 .sbr 檔。  當您建置或更新瀏覽資訊檔時，專案中所有的 .sbr 檔都必須在磁碟中。  
  
 若要建立包含所有可能資訊的 .sbr 檔，可以指定 [\/FR](../../build/reference/fr-fr-create-dot-sbr-file.md)。  
  
 若要建立不包含區域符號的 .sbr 檔，可以指定 [\/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md)。  如果 .sbr 檔中已經包含了區域符號，您還是可以利用 BSCMAKE 的 [\/El 選項](../../build/reference/bscmake-options.md)在 .bsc 檔中將它們省略`。`  
  
 您不需執行完整的編譯，就可以建立 .sbr 檔。  例如，可以對編譯器指定 \/Zs 選項以執行語法檢查，且仍可以產生一個 .sbr 檔，如果指定 \/FR 或 \/Fr 的話。  
  
 如果先將 .sbr 檔封裝以移除未參考定義，建置過程會更有效率。  編譯器會自動封裝 .sbr 檔。  
  
## 請參閱  
 [建置 .Bsc 檔](../../build/reference/building-a-dot-bsc-file.md)