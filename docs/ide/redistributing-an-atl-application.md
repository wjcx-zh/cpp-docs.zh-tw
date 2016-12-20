---
title: "轉散發 ATL 應用程式 | Microsoft Docs"
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
  - "ATL, 轉散發"
  - "OLE DB 樣板, 轉散發"
  - "轉散發 ATL"
  - "轉散發 OLE DB 樣板"
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 轉散發 ATL 應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Visual Studio 2012 開始，Active Template Library \(ATL\) 是僅限標頭的程式庫。  ATL 專案不會動態連結至 ATL 選項。  可轉散發 ATL 程式庫不是必要的。  
  
 如果您轉散發 ATL 可執行的應用程式，即必須發出下列命令來註冊 .exe 檔案 \(和其中所有控制項\)：  
  
```  
filename /regserver  
  
```  
  
 其中 `filename` 是可執行檔案的名稱。  
  
 在 Visual Studio 2010 中，ATL 專案可以建置成 MinDependency 或 MinSize 組態。  當您在 \[一般\] 屬性頁上將 \[ATL 用法\] 屬性設為 \[靜態連結 ATL\]，在 \[程式碼產生\] 屬性頁 \(C\/C\+\+ 資料夾\) 上將 \[執行階段程式庫\] 屬性設為 \[多執行緒 \(\/MT\)\] 時，MinDependency 組態就是您得到的結果。  
  
 當您在 \[一般\] 屬性頁上將 \[ATL 用法\] 屬性設為 \[動態連結 ATL\]，或在 \[程式碼產生\] 屬性頁 \(C\/C\+\+ 資料夾\) 上將 \[執行階段程式庫\] 屬性設為 \[多執行緒 DLL \(\/MD\)\] 時，MinSize 組態就是您得到的結果。  
  
 MinSize 會讓輸出檔案盡可能的小，但目標電腦上需要有 ATL100.dll 和 Msvcr100.dll \(如果您選取 \[多執行緒 DLL \(\/MD\)\] 選項\)。  ATL100.dll 應該在目標電腦上註冊，以確保所有 ATL 的功能都會出現。  ATL100.dll 包含 ANSI 和 Unicode 匯出。  
  
 如果為 MinDependency 目標建置 ATL 或 OLE DB 範本專案，目標電腦上不必安裝和註冊 ATL100.dll，雖然您可能會得到較大的程式映像。  
  
 至於 OLE DB 範本應用程式，請確定目標電腦有最新版的 Microsoft Data Access Components \(MDAC\) 檔案。  如需詳細資訊，請參閱[轉散發資料庫支援檔案](../ide/redistributing-database-support-files.md)。  
  
## 請參閱  
 [轉散發 Visual C\+\+ 檔案](../ide/redistributing-visual-cpp-files.md)