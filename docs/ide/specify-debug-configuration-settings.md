---
title: 新的專案，從現有程式碼偵錯設定 （Visual c + +） |Microsoft 文件
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
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>從現有的程式碼檔建立新專案精靈、指定偵錯組態設定
使用 從現有的程式碼檔建立新專案精靈的這個頁面來指定偵錯組態專案設定。  
  
## <a name="task-list"></a>工作清單  
 [如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **建置命令列**  
 指定命令列建置新專案。 例如，輸入編譯器 （加上任何參數和引數） 的名稱，或您想要用來建置新專案的建置指令碼。 會啟用此選項時**使用外部建置系統**中選取選項**指定專案設定**頁面; 否則就無法使用。  
  
 **重建命令列**  
 指定命令列，會重建新的專案。 會啟用此選項時**使用外部建置系統**中選取選項**指定專案設定**頁面; 否則就無法使用。  
  
 **清除命令列**  
 指定要刪除新的專案的建置工具所產生的支援檔案的命令列。 會啟用此選項時**使用外部建置系統**中選取選項**指定專案設定**頁面; 否則就無法使用。  
  
 **輸出 （適用於偵錯）**  
 指定新專案的偵錯組態的輸出檔的目錄路徑。 會啟用此選項時**使用外部建置系統**中選取選項**指定專案設定**頁面; 否則就無法使用。  
  
 **前置處理器定義 (/ D)**  
 定義前置處理器符號為新的專案。 如需詳細資訊，請參閱 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。  
  
 **包含搜尋路徑 (/ I)**  
 指定要加入的編譯器要搜尋的目錄清單來解析檔案參考傳遞至新的專案中的前置處理器指示詞的目錄路徑。 如需詳細資訊，請參閱 [/I (其他 Include 目錄)](../build/reference/i-additional-include-directories.md)。  
  
 **強制包含的檔案 (/FI)**  
 指定要處理時建置新專案的標頭檔案。 如需詳細資訊，請參閱 [/FI (指定強制的 Include 檔)](../build/reference/fi-name-forced-include-file.md)。  
  
 **.NET 組件搜尋路徑 (/ AI)**  
 指定的目錄路徑，編譯器會搜尋解析.NET 組件的參考傳遞給新的專案中的前置處理器指示詞。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](../build/reference/ai-specify-metadata-directories.md)。  
  
 **強制使用.NET 組件 (/ FU)**  
 指定要處理時建置新專案的.NET 組件。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](../build/reference/fu-name-forced-hash-using-file.md)。  
  
## <a name="see-also"></a>另請參閱  
 [從現有的程式碼檔建立新專案精靈、指定專案設定](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)
