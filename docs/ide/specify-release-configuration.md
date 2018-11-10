---
title: 從現有程式碼新增專案發行組態
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.releasesettings
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
ms.openlocfilehash: 10dec5e36531c9c0bf549b37bbfa892a624d0bf0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511811"
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>從現有的程式碼檔建立新專案精靈、指定發行組態設定

使用 [從現有程式碼檔案建立新專案精靈] 的這個頁面，來指定發行組態專案設定。

## <a name="task-list"></a>工作清單

[如何：從現有程式碼建立 C++ 專案](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>UIElement 清單

- **與偵錯組態相同**

   指定精靈將產生與偵錯組態專案設定相同的發行組態專案設定。 預設會核取這個選項。 除非您取消核取此方塊，否則此頁面上的所有其他選項都處於非使用中狀態。

- **Build 命令列**

   指定此命令列可建置新專案。 輸入編譯器的名稱，加上您想要用來建置新專案的任何參數或引數。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項。

- **Rebuild 命令列**

   指定此命令列可重建新專案。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項。

- **Clean 命令列**

   指定此命令列可刪除建置工具為新專案產生的支援檔案。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項。

- **輸出 (偵錯用)**

   為新專案的偵錯組態指定輸出檔的目錄路徑。 在 [指定專案設定] 頁面中選取 [使用外部建置系統] 選項時，就會啟用此選項。

- **前置處理器定義 (/D)**

   定義新專案的前置處理器符號。 如需詳細資訊，請參閱 [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md)。

- **包含搜尋路徑 (/I)**

   指定要新增至目錄清單的目錄路徑，編譯器將會搜尋這些路徑，以解析傳遞至新專案中前置處理器指示詞的檔案參考。 如需詳細資訊，請參閱 [/I (其他 Include 目錄)](../build/reference/i-additional-include-directories.md)。

- **強制包含的檔案 (/FI)**

   指定建置新專案時要處理的標頭檔。 如需詳細資訊，請參閱 [/FI (指定強制的 Include 檔)](../build/reference/fi-name-forced-include-file.md)。

- **.NET 組件搜尋路徑 (/AI)**

   指定目錄路徑，編譯器將會搜尋這些路徑，以解析傳遞至新專案中前置處理器指示詞的 .NET 組件參考。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](../build/reference/ai-specify-metadata-directories.md)。

- **強制使用 .NET 組件 (/FU)**

   指定建置新專案時要處理的 .NET 組件。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](../build/reference/fu-name-forced-hash-using-file.md)。

## <a name="see-also"></a>請參閱

[從現有的程式碼檔建立新專案精靈、指定專案設定](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)