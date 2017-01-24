---
title: "/DEBUGTYPE (偵錯資訊選項) | Microsoft Docs"
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
  - "/debugtype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEBUGTYPE 連結器選項"
  - "DEBUGTYPE 連結器選項"
  - "-DEBUGTYPE 連結器選項"
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DEBUGTYPE (偵錯資訊選項)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/DEBUGTYPE 選項指定 \/DEBUG 選項所產生的偵錯資訊類型。  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## 引數  
 CV  
 通知連結器發出符號、行號和 PDB 檔案中其他物件編譯資訊的偵錯資訊。  根據預設，指定 **\/DEBUG** 和未指定 **\/DEBUGTYPE** 時會啟用此選項。  
  
 PDATA  
 通知連結器將 .pdata 和 .xdata 項目加入至 PDB 檔案中的偵錯資料流資訊。  根據預設，同時指定 **\/DEBUG** 和 **\/DRIVER** 時會啟用此選項。  如果自行指定 **\/DEBUGTYPE:PDATA**，連結器會自動在 PDB 檔案中包含偵錯符號。  如果已指定 **\/DEBUGTYPE:PDATA,FIXUP**，連結器不會在 PDB 檔案中包含偵錯符號。  
  
 FIXUP  
 通知連結器將重新配置資料表項目加入至 PDB 檔案中的偵錯資料流資訊。  根據預設，同時指定 **\/DEBUG** 和 **\/PROFILE** 時會啟用此選項。  如果已指定 **\/DEBUGTYPE:FIXUP** 或 **\/DEBUGTYPE:FIXUP,PDATA**，連結器不會在 PDB 檔案中包含偵錯符號。  
  
 **\/DEBUGTYPE** 的引數可能會以任何順序結合，並以逗號分隔。  **\/DEBUGTYPE** 選項及其引數不區分大小寫。  
  
## 備註  
 使用 **\/DEBUGTYPE** 選項，以指定在偵錯資料流中包含重新配置資料表資料或 .pdata 和 .xdata 標頭資訊。  這會使連結器包含使用者模式程式碼的相關資訊，當核心模式程式碼中斷時，該資訊可以在核心偵錯工具中顯示。  若要讓偵錯符號在已指定 **FIXUP** 時可供使用，請包含 **CV** 引數。  
  
 若要在使用者模式中偵錯程式碼 \(這是應用程式的常見情形\)，則不需要 **\/DEBUGTYPE** 選項。  根據預設，指定偵錯輸出的編譯器參數 \([\/Z7、\/Zi、\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)\) 會發出 Visual Studio 偵錯工具所需的所有資訊。  使用 **\/DEBUGTYPE:PDATA** 或 **\/DEBUGTYPE:CV,PDATA,FIXUP** 以偵錯程式碼，該程式碼結合使用者模式和核心模式元件，例如裝置驅動程式的組態應用程式。  如需有關核心模式偵錯工具的詳細資訊，請參閱 [Windows 的偵錯工具 \(WinDbg、KD、CDB、NTSD\)](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## 請參閱  
 [\/DEBUG \(產生偵錯資訊\)](../../build/reference/debug-generate-debug-info.md)   
 [\/DRIVER \(Windows NT 核心模式驅動程式\)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [\/PROFILE \(效能工具分析工具\)](../../build/reference/profile-performance-tools-profiler.md)   
 [Windows 的偵錯工具 \(WinDbg、KD、CDB、NTSD\)](http://go.microsoft.com/fwlink/p?LinkID=285651)