---
title: "如何：在 Makefile 專案中啟用 IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCNMakeTool.IntelliSense"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IntelliSense, Makefile 專案"
  - "Makefile 專案, IntelliSense"
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：在 Makefile 專案中啟用 IntelliSense
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若未正確設定特定專案設定或編譯器選項，IntelliSense 便無法在 Visual C\+\+ Makefile 專案的 IDE 中操作。  請使用這個程序設定 Visual C\+\+ Makefile 專案，如此一來，當 Makefile 專案在 Visual Studio 開發環境中開啟時，IntelliSense 就能順利運作。  
  
### 若要在 IDE 中為 Makefile 專案啟用 IntelliSense  
  
1.  開啟 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  選取 \[**NMake**\] 屬性頁，然後適當地修改 \[**IntelliSense**\] 下的屬性。  
  
    -   設定讓 \[**前置處理器定義**\] 屬性定義 Makefile 專案中的任何前置處理器符號。  如需詳細資訊，請參閱 [\/D \(前置處理器定義\)](../build/reference/d-preprocessor-definitions.md)。  
  
    -   設定 \[**包含搜尋路徑**\] 屬性以指定編譯器將要搜尋的目錄清單，進而解析傳遞至 Makefile 專案中前置處理器指示詞的檔案參考。  如需詳細資訊，請參閱 [\/I \(其他 Include 目錄\)](../build/reference/i-additional-include-directories.md)。  
  
         針對使用 \[命令視窗\] 中的 CL.EXE 建置的專案，請設定讓 \[**INCLUDE**\] 環境變數指定編譯器將在其中搜尋的目錄，以解析傳遞至 Makefile 專案中前置處理器指示詞的檔案參考。  
  
    -   設定讓 \[**強制包含**\] 屬性指定建置 Makefile 專案時要處理的標頭檔。  如需詳細資訊，請參閱 [\/FI \(命名強制的包含檔\)](../build/reference/fi-name-forced-include-file.md)。  
  
    -   設定讓 \[**組件搜尋路徑**\] 屬性指定目錄清單，編譯器將在該清單中搜尋，以解析專案中 .NET 組件的參考。  如需詳細資訊，請參閱 [\/AI \(指定中繼資料目錄\)](../build/reference/ai-specify-metadata-directories.md)。  
  
    -   設定讓 \[**強制使用組件**\] 屬性指定建置 Makefile 專案時要處理的 .NET 組件。  如需詳細資訊，請參閱 [\/FU \(命名強制的 \#using 檔案\)](../build/reference/fu-name-forced-hash-using-file.md)。  
  
    -   設定 \[**其他選項**\] 屬性，以指定 Intellisense 在剖析 C\+\+ 檔案時所要使用的其他編譯器參數。  
  
4.  按一下 \[**確定**\] 關閉屬性頁。  
  
5.  使用 \[**全部儲存**\] 命令儲存修改過的專案設定。  
  
 下一次在 Visual Studio 開發環境中開啟 Makefile 專案時，請在 Makefile 專案上執行 \[**清除方案**\] 命令，再執行 \[**建置方案**\] 命令。  IntelliSense 應能在 IDE 中正常運作。  
  
## 請參閱  
 [使用 IntelliSense](../Topic/Using%20IntelliSense.md)   
 [NMAKE 參考](../build/nmake-reference.md)   
 [如何：從現有程式碼建立 C\+\+ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)