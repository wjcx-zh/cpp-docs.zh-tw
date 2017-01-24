---
title: "/FD (IDE 最少重建) | Microsoft Docs"
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
  - "/FD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FD 編譯器選項 [C++]"
  - "FD 編譯器選項 [C++]"
  - "-FD 編譯器選項 [C++]"
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FD (IDE 最少重建)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/FD** 並不向使用者公開 \(但 C\+\+ 專案之 \[**屬性頁**\] 對話方塊的[命令列](../../ide/command-line-property-pages.md)屬性頁中除外\)，除非未同時選取 [\/Gm \(啟用最少重建\)](../../build/reference/gm-enable-minimal-rebuild.md)。  **\/FD** 除了從開發環境以外，也沒有任何效用。  **\/FD** 並不在 **cl \/?** 的輸出中公開。  
  
 如果不在開發環境中啟用 **\/Gm**，就會使用 **\/FD**。  **\/FD** 會確保 .idb 檔有足夠的相依性資訊。  **\/FD** 只會由開發環境使用，而且不可以從命令列或建置指令檔加以使用。  
  
## 請參閱  
 [輸出檔 \(\/F\) 選項](../../build/reference/output-file-f-options.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)