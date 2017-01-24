---
title: "BSCMAKE 如何建置 .Bsc 檔 | Microsoft Docs"
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
  - "瀏覽資訊檔 (.bsc), 建置"
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 如何建置 .Bsc 檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

BSCMAKE 會盡可能以最有效的方式建置或重建 .bsc 檔案。  若要避免潛在的問題，瞭解建置程序非常重要。  
  
 當 BSCMAKE 建置瀏覽資訊檔時，會將 .sbr 檔的長度截斷為零。  之後在建置同一個檔案時，長度為零的 \(或空的\) .sbr 檔會告訴 BSCMAKE，.sbr 檔沒有被修改。  它讓 BSCMAKE 知道不需要更新那部分的檔案，只需累加建置 \(Incremental Build\) 即可。  在每一次建置期間 \(除非指定 \/n 選項\)，BSCMAKE 會先試著只以變更過的 .sbr 檔對檔案進行累加更新。  
  
 BSCMAKE 會尋找擁有 \/o 選項所指定名稱的 .bsc 檔。  沒有指定 \/o 時，BSCMAKE 會尋找主檔名 \(Base Name\) 與第一個 .sbr 檔相同且副檔名為 .bsc 的檔案。  檔案存在時，BSCMAKE 會只使用提供的 .sbr 檔進行瀏覽資訊檔的累加建置。  如果檔案不存在，BSCMAKE 會使用所有的 .sbr 檔進行完整建置。  建置規則如下：  
  
-   若要成功地執行完整建置，所有指定的 .sbr 檔都必須存在，而且不可以被截斷。  如果有 .sbr 檔被截斷，則必須在執行 BSCMAKE 之前重建 \(重新編譯或組譯\) 這個檔案。  
  
-   若要成功地執行累加建置，.bsc 檔必須存在。  所有提供的 .sbr 檔，甚至空的檔案，都必須存在且必須在 BSCMAKE 命令列中指定。  如果您在命令列中省略了某個 .sbr 檔，BSCMAKE 會在檔案中將它的成果移除。  
  
## 請參閱  
 [建置 .Bsc 檔](../../build/reference/building-a-dot-bsc-file.md)