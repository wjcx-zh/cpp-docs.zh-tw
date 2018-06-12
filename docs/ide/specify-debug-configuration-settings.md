---
title: 從現有程式碼新增專案的偵錯設定 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.debugsettings
dev_langs:
- C++
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b40bafe817ebf1dd25cc40115635b895502e0df8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33335038"
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>從現有的程式碼檔建立新專案精靈、指定偵錯組態設定
使用 [從現有的程式碼檔建立新專案精靈] 的這個頁面，來指定偵錯組態專案設定。  
  
## <a name="task-list"></a>工作清單  
 [如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **Build 命令列**  
 指定此命令列可建置新專案。 例如，輸入編譯器的名稱 (加上任何參數和引數)，或您想要用來建置新專案的建置指令碼。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項；否則無法使用此選項。  
  
 **Rebuild 命令列**  
 指定此命令列可重建新專案。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項；否則無法使用此選項。  
  
 **Clean 命令列**  
 指定此命令列可刪除建置工具為新專案產生的支援檔案。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項；否則無法使用此選項。  
  
 **輸出 (偵錯用)**  
 為新專案的偵錯組態指定輸出檔的目錄路徑。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項；否則無法使用此選項。  
  
 **前置處理器定義 (/D)**  
 定義新專案的前置處理器符號。 如需詳細資訊，請參閱 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。  
  
 **包含搜尋路徑 (/I)**  
 指定要新增至目錄清單的目錄路徑，編譯器將會搜尋這些路徑，以解析傳遞至新專案中前置處理器指示詞的檔案參考。 如需詳細資訊，請參閱 [/I (其他 Include 目錄)](../build/reference/i-additional-include-directories.md)。  
  
 **強制包含的檔案 (/FI)**  
 指定建置新專案時要處理的標頭檔。 如需詳細資訊，請參閱 [/FI (指定強制的 Include 檔)](../build/reference/fi-name-forced-include-file.md)。  
  
 **.NET 組件搜尋路徑 (/AI)**  
 指定目錄路徑，編譯器將會搜尋這些路徑，以解析傳遞至新專案中前置處理器指示詞的 .NET 組件參考。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](../build/reference/ai-specify-metadata-directories.md)。  
  
 **強制使用 .NET 組件 (/FU)**  
 指定建置新專案時要處理的 .NET 組件。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](../build/reference/fu-name-forced-hash-using-file.md)。  
  
## <a name="see-also"></a>請參閱  
 [從現有的程式碼檔建立新專案精靈、指定專案設定](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)
