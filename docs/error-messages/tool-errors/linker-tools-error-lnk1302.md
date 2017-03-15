---
title: "連結器工具錯誤 LNK1302 | Microsoft Docs"
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
  - "LNK1302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1302"
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1302
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

僅支援連結 safe .netmodules，無法連結 .netmodule 檔  
  
 在使用者嘗試叫用的 MSIL 連結時，傳遞 .netmodule \(以 **\/LN** 編譯\) 給連結器。C\+\+ 模組只有在以 **\/clr:safe** 編譯時，才會對 MSIL 連結有效。  
  
 若要更正這項錯誤，請以 **\/clr:safe** 編譯，以便啟用 MSIL 連結，或是傳遞 **\/clr** 或 **\/clr:pure** .obj 檔取代模組給連結器。  
  
 如需詳細資訊，請參閱  
  
-   [\/LN \(建立 MSIL 模組\)](../../build/reference/ln-create-msil-module.md)  
  
-   [.netmodule 檔做為連結器輸入](../../build/reference/netmodule-files-as-linker-input.md)