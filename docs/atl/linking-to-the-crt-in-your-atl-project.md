---
title: "Linking to the CRT in Your ATL Project | Microsoft Docs"
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
  - "DllMainCRTStartup"
  - "wWinMainCRTStartup"
  - "WinMainCRTStartup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, C Run-Time library (CRT)"
  - "CRT, linking with ATL"
  - "DllMainCRTStartup method"
  - "WinMainCRTStartup method"
  - "wWinMainCRTStartup method"
ms.assetid: 650957ae-362c-4ecf-8b03-5d49138e8b5b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Linking to the CRT in Your ATL Project
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[C 執行階段程式庫](../c-runtime-library/crt-library-features.md) \(CRT\) ATL 提供在開發期間，可以使程式設計更容易許多有用的功能。  所有的 ATL 專案連結至 CRT 程式庫。  您可以看到連接在 [使用方法的優點和交易連結至 CRT](../atl/benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt.md)方法的優點和缺點。  
  
## 連接的效果與 CRT 對程式影像  
 如果您是使用 CRT 靜態連結的 CRT，從程式碼中的可執行檔映像上，而且您不需要 CRT DLL 在執行影像的系統。  如果您是使用 CRT 動態連接，對程式碼的參考 CRT DLL 中，影像，而非程式碼不具有位置。  為了讓您的影像可以在特定系統， CRT DLL 必須存在於該系統。  即使您使用 CRT 動態連接時，您可能會發現某些程式碼可以靜態連接 \(例如， **DllMainCRTStartup**\)。  
  
 當您連結您的影像時，您也會明確或隱含指定作業系統將呼叫載入影像之後的進入點。  對於 DLL，預設進入點是 **DllMainCRTStartup**。  對於 EXE，它是 **WinMainCRTStartup**。  您可以覆寫以\/ENTRY 連結器選項的預設值。  CRT 針對 **DllMainCRTStartup**、 **WinMainCRTStartup**和 **wWinMainCRTStartup** \(EXE 的 Unicode 進入點的實作\)。  這些在全域物件提供了 CRT 進入點呼叫建構函式並初始化有些 CRT 函式使用的其他資料結構。  如果靜態連接，則這個啟始程式碼會將有關 25K 加入影像。  如果使用動態連結，大多數程式碼在 DLL，如此一來，您的影像大小最小。  
  
 如需詳細資訊，請參閱連結器主題 [\/ENTRY \(進入點符號\)](../build/reference/entry-entry-point-symbol.md)。  
  
## 最佳化選項  
 使用連結器選項\/OPT: NOWIN98 能 10K 進一步減少預設 ATL 控制項，在消耗 Windows 98 系統上的載入時間。  如需連接選項的詳細資訊，請參閱 [\/OPT \(最佳化\)](../build/reference/opt-optimizations.md)。  
  
## 請參閱  
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../atl/programming-with-atl-and-c-run-time-code.md)   
 [執行階段程式庫行為](../build/run-time-library-behavior.md)