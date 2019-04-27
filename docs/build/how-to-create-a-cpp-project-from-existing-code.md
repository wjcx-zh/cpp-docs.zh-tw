---
title: HOW TO：從現有的程式碼建立 C++ 專案
ms.date: 01/15/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 1658e19595d8cfc7966ca881abfdd2aa8acf76ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62189010"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>HOW TO：從現有的程式碼建立 C++ 專案

在 Visual Studio 中，您可以使用 [從現有程式碼檔建立新專案精靈] 將現有的程式碼檔移植到 C++ 專案。 此精靈會建立專案解決方案，其使用 MSBuild 系統管理來源檔案和組建組態。 最適合用於不具有複雜資料夾階層的較簡易專案。 在 Visual Studio 的舊版 Express 中無法使用此精靈。 

將現有的程式碼檔移植到 C++ 專案，可讓您使用 IDE 內建的原生 MSBuild 專案管理功能。 如果您想要使用現有的建置系統，例如 nmake makefile、CMake 或其他選項，可以改用 [開啟] > [資料夾] 或 [CMake] 選項。 如需詳細資訊，請參閱 <<c0> [ 專案開啟資料夾C++](open-folder-projects-cpp.md)或是[Visual Studio 中的 CMake 專案](cmake-projects-in-visual-studio.md)。</c0> 這兩個選項都可讓您使用 IDE 功能，例如 [IntelliSense](/visualstudio/ide/using-intellisense) 和[專案屬性](working-with-project-properties.md)。

### <a name="to-create-a-c-project-from-existing-code"></a>若要從現有程式碼建立 C++ 專案

1. 在 [檔案] 功能表上，選取 [新增] > [來自現有程式碼的專案]。

1. 在 [從現有的程式碼檔建立新專案精靈] 的第一頁，於 [您要建立的專案類型為何] 清單中選取 [Visual C++]。 選擇 [下一步]  繼續進行。

1. 指定專案的位置、來源檔案的目錄，以及精靈要匯入新專案的檔案種類。 選擇 [下一步]  繼續進行。

    | 設定 | 描述 |
    | --- | --- |
    | [專案檔位置] | 指定新專案的目錄路徑。 這裡是精靈儲放新專案所有檔案 (和子目錄) 的位置。<br/><br/>選取 [瀏覽] 以顯示 [專案檔位置] 對話方塊。 巡覽至正確的資料夾，然後指定包含新專案的目錄。 |
    | **專案名稱** | 指定新專案的名稱。 具有 .vcxproj 這類副檔名的專案檔會採用此名稱，現有的程式碼檔則保留其原始名稱。 |
    | [從這些資料夾將檔案新增至專案] | 選取即可設定精靈，使其將原始目錄 (在此控制項下方的清單方塊中指定) 的現有程式碼檔複製到新專案中。<br/><br/>選取 [新增子資料夾]，以指定將其所有子目錄的程式碼檔複製到專案中。 目錄列於 [資料夾] 欄位中。<br/>- 選取 [新增] 即可顯示 [從這個資料夾將檔案新增到專案中] 對話方塊，以指定精靈要在其中搜尋現有程式碼檔的目錄。<br/>- 選取 [移除] 以刪除清單方塊中選取的目錄路徑。<br/><br/>在 [要新增到專案的檔案類型] 方塊中，指定精靈要根據指定副檔名新增到新專案的檔案種類。 副檔名前面會加上星號萬用字元，並在副檔名清單中以分號分隔。 |
    | **在方案總管中顯示所有檔案** | 指定要在 [方案總管] 視窗中顯示新專案中的所有檔案。 這個選項預設為啟用。 |

    ![專案位置](media/location.png)

1. 指定要使用的專案設定 (例如新專案的建置環境) 及建置設定，以比對要產生的特定類型新專案。 選擇 [下一步]  繼續進行。

    | 設定 | 描述 |
    | --- | --- |
    | **使用 Visual Studio** | 指定使用 Visual Studio 隨附的建置工具來建置新的專案。 預設會選取這個選項。<br/><br/>選取 [專案類型] 以指定精靈產生的專案類型。 選擇 [Windows 應用程式專案]、[主控台應用程式專案]、[動態連結程式庫 (DLL) 專案] 或 [靜態程式庫 (LIB) 專案]。<br/><br/>選取 [新增 ATL 的支援] 以將 ATL 支援新增至新專案。<br/><br/>選取 [新增 MFC 的支援] 以將 MFC 支援新增至新專案。<br/><br/>選取 [新增通用語言執行平台的支援] 以將 CLR 程式設計的支援新增至專案。 為合規性類型選擇 [通用語言執行平台支援]，例如選擇 [通用語言執行平台 (舊語法)]代表符合 Managed Extensions for C++ 語法 (Visual C++ 2005 之前的 CLR 程式設計語法) 的規範。 |
    | **使用外部建置系統** | 指定使用未隨附於 Visual Studio 的建置工具來建置新專案。 選取此選項時，您可以在 [指定偵錯組態設定] 和 [指定發行組態設定] 頁面上指定建置命令行。 |

    ![專案設定](media/settings.png)

    > [!NOTE]
    > 選取 [使用外部建置系統] 選項時，IDE 不會建置專案，因此不需要 /D、/I、/FI、/AI 或 /FU 選項即可進行編譯。 不過，您必須正確設定這些選項，IntelliSense 才能正常運作。

1. 指定要使用的偵錯組態設定。 選擇 [下一步]  繼續進行。

    | 設定 | 描述 |
    | --- | --- |
    | **Build 命令列** | 指定此命令列可建置專案。 輸入編譯器的名稱 (加上任何參數或引數)，或您想要用來建置專案的建置指令碼。 |
    | **Rebuild 命令列** | 指定此命令列可重建新專案。 |
    | **Clean 命令列** | 指定此命令列可刪除建置工具為專案產生的支援檔案。 |
    | **輸出 (偵錯用)** | 為專案的偵錯組態指定輸出檔案的目錄路徑。 |
    | **前置處理器定義 (/D)** | 定義專案的前置處理器符號，請參閱 [/D (前置處理器定義)](../build/reference/d-preprocessor-definitions.md)。 |
    | **包含搜尋路徑 (/I)** | 指定目錄路徑，編譯器會搜尋這些路徑，以解析傳遞至專案中前置處理器指示詞的檔案參考，請參閱 [/I (其他 Include 目錄)](../build/reference/i-additional-include-directories.md)。 |
    | **強制包含的檔案 (/FI)** | 指定建置專案時要處理的標頭檔，請參閱 [/FI (指定強制的 Include 檔)](../build/reference/fi-name-forced-include-file.md)。 |
    | **.NET 組件搜尋路徑 (/AI)** | 指定目錄路徑，編譯器會搜尋這些路徑，以解析傳遞至專案中前置處理器指示詞的 .NET 組件參考，請參閱 [/AI (指定中繼資料目錄)](../build/reference/ai-specify-metadata-directories.md)。 |
    | **強制使用 .NET 組件 (/FU)** | 指定建置專案時要處理的 .NET 組件，請參閱 [/FU (指定強制的 #using 檔案)](../build/reference/fu-name-forced-hash-using-file.md)。 |

    ![專案組態](media/config.png)

    > [!NOTE]
    > 只有在 [指定專案設定] 頁面上選取了 [使用外部建置系統] 選項時，才會啟用 **Build**、**Rebuild**、**Clean** 命令列，以及**輸出 (偵錯用)** 設定。

1. 指定要使用的發行組態設定，這些設定與偵錯組態設定相同。 選擇 [完成] 產生新專案。

    > [!NOTE]
    > 您可在這裡選取 [與偵錯組態相同]，以指定精靈將產生與偵錯組態專案設定相同的發行組態專案設定。 預設會核取這個選項。 除非您取消核取此方塊，否則此頁面上的所有其他選項都處於非使用中狀態。
