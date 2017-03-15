---
title: "從現有的程式碼檔建立新專案精靈、指定偵錯組態設定 | Microsoft Docs"
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
  - "vc.appwiz.importwiz.debugsettings"
dev_langs: 
  - "C++"
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從現有的程式碼檔建立新專案精靈、指定偵錯組態設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 \[從現有的程式碼檔建立新專案\] 精靈的這個頁面指定偵錯組態專案設定。  
  
## 工作清單  
 [如何：從現有程式碼建立 C\+\+ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## UIElement 清單  
 **建置命令列**  
 指定建置新專案的命令列。  例如，輸入編譯器名稱 \(以及任何參數或引數\) 或要用來建置新專案的建置指令碼。  當 \[**指定專案設定**\] 頁上選取 \[**使用外部建置系統**\] 選項時，才會啟用這個選項，否則無法使用。  
  
 **重建命令列**  
 指定重建新專案的命令列。  當 \[**指定專案設定**\] 頁上選取 \[**使用外部建置系統**\] 選項時，才會啟用這個選項，否則無法使用。  
  
 **清除命令列**  
 指定讓命令列刪除新專案建置工具所產生的支援檔案。  當 \[**指定專案設定**\] 頁上選取 \[**使用外部建置系統**\] 選項時，才會啟用這個選項，否則無法使用。  
  
 **輸出 \(用於偵錯\)**  
 指定新專案的偵錯組態所使用的輸出檔目錄路徑。  當 \[**指定專案設定**\] 頁上選取 \[**使用外部建置系統**\] 選項時，才會啟用這個選項，否則無法使用。  
  
 **前置處理器定義 \(\/D\)**  
 定義新專案的前置處理器符號。  如需詳細資訊，請參閱 [\/D \(前置處理器定義\)](../build/reference/d-preprocessor-definitions.md)。  
  
 **包含搜尋路徑 \(\/I\)**  
 指定要加入至編譯器會在其中搜尋之目錄清單的目錄路徑，以解析傳遞至新專案中前置處理器指示詞的檔案參考。  如需詳細資訊，請參閱 [\/I \(其他 Include 目錄\)](../build/reference/i-additional-include-directories.md)。  
  
 **強制包含的檔案 \(\/FI\)**  
 指定建置新專案時要處理的標頭檔。  如需詳細資訊，請參閱 [\/FI \(命名強制的包含檔\)](../build/reference/fi-name-forced-include-file.md)。  
  
 **.NET 組件搜尋路徑 \(\/AI\)**  
 指定編譯器會在其中搜尋的目錄路徑，以解析傳遞至新專案中前置處理器指示詞的 .NET 組件參考。  如需詳細資訊，請參閱 [\/AI \(指定中繼資料目錄\)](../build/reference/ai-specify-metadata-directories.md)。  
  
 **強制使用 .NET 組件 \(\/FU\)**  
 指定建置新專案時要處理的 .NET 組件。  如需詳細資訊，請參閱 [\/FU \(命名強制的 \#using 檔案\)](../build/reference/fu-name-forced-hash-using-file.md)。  
  
## 請參閱  
 [從現有的程式碼檔建立新專案精靈、指定專案設定](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)