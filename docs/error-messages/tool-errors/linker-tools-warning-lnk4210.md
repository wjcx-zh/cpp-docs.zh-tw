---
title: "連結器工具警告 LNK4210 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4210"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4210"
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 連結器工具警告 LNK4210
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

section 區段存在，可能有未處理的靜態初始設定式或終止函式  
  
 某段程式碼引入了靜態初始設定式或終止函式，但應用程式啟動時並未執行 CRT 或其對等用法 \(這需要執行靜態初始設定式或終止函式\)。  會導致此結果的程式碼範例：  
  
-   有建構函式、解構函式或虛擬函式表的全域類別變數。  
  
-   全域變數以一個非編譯時間的常數加以初始化。  
  
 若要修正這個問題，請嘗試下列任一種方法：  
  
-   移除所有包含靜態初始設定式的程式碼。  
  
-   不要使用 [\/NOENTRY](../../build/reference/noentry-no-entry-point.md)。在移除 \/NOENTRY 之後，可能也必須將 msvcrt.lib、libcmt.lib 或 libcmtd.lib 加入您的連結器命令列。  
  
-   加入 msvcrt.lib、libcmt.lib 或 libcmtd.lib 至您的連結器命令列。  
  
-   從 \/clr:pure 編譯移到 \/clr 時，請移除連結器列的 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 選項。  這樣會啟用 CRT 初始設定，使應用程式啟動時會執行靜態初始設定式。  
  
-   如果您的專案是以 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 建置，而且如果是傳遞了函式給 \/ENTRY，而不是傳遞 `_DllMainCRTStartup`，則該函式必須呼叫 CRT\_INIT。  請參閱 [執行階段程式庫行為](../../build/run-time-library-behavior.md) 和知識庫文件 Q94248， [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;94248](http://support.microsoft.com/default.aspx?scid=kb;en-us;94248) 以取得詳細資訊。  
  
 [\/GS](../../build/reference/gs-buffer-security-check.md) 編譯器選項需要 CRT 啟始程式碼。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)