---
title: "編譯器錯誤 C3505 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3505"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3505"
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3505
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法載入型別程式庫 'guid'  
  
 如果您是在 64 位元電腦上執行 \(32 位元至\) 64 位元跨平台編譯器可能會造成 C3505 錯誤，因為編譯器是在 WOW64 之下執行，而且只能讀取 32 位元登錄區。  
  
 您可以透過建置嘗試要匯入並同時登錄的 32 位元和 64 位元版的型別程式庫，解決 C3505 的問題。或者，您也可以使用原生 64 位元編譯器，但這樣就需要將 IDE 中的 VC\+\+ 目錄變更為指向 64 位元編譯器。  
  
 如需詳細資訊，請參閱：  
  
-   [如何：在命令列啟用 64 位元 Visual C\+\+ 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [如何：在命令列啟用 64 位元 Visual C\+\+ 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [如何：將 Visual C\+\+ 專案設定成以 64 位元平台為目標](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)