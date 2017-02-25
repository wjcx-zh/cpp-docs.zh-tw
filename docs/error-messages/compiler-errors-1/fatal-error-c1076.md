---
title: "嚴重錯誤 C1076 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1076"
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 嚴重錯誤 C1076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制：已達到內部堆積限制；請使用 \/Zm 以指定更高的限制  
  
 這項錯誤可能會因為符號太多或樣板具現化太多而產生。  
  
 若要解決這個錯誤：  
  
1.  使用 [\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) 選項將編譯器記憶體限制設定為 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) 錯誤訊息中指定的值。  如需包含如何在 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 中設定此值的詳細資訊，請參閱 [\/Zm \(指定先行編譯標頭檔的記憶體配置上限\)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) 中的＜備註＞一節。  
  
2.  如果您是在 64 位元作業系統上使用 32 位元裝載的編譯器，請改用 64 位元裝載的編譯器。  如需詳細資訊，請參閱 [如何：在命令列啟用 64 位元 Visual C\+\+ 工具組](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)。  
  
3.  排除不必要的包含檔案。  
  
4.  排除不必要的全域變數，例如動態地配置記憶體，而不宣告大型陣列。  
  
5.  排除未使用到的宣告。  
  
6.  將大型函式分割成較小的函式。  
  
7.  將大型類別分割成較小的類別。  
  
8.  將目前的檔案分割成較小的檔案。  
  
 如果建置開始之後馬上出現 C1076 錯誤，可能是 **\/Zm** 所指定的值對程式而言太高了。  請降低 **\/Zm** 值。