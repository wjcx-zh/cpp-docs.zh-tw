---
title: 在 Visual Studio 中建立 C++ Makefile 專案
ms.date: 08/05/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects [C++]
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: a712b6da89433b9db6de9f2a676bf6e89d2e0e6e
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560814"
---
# <a name="create-a-c-makefile-project"></a>建立 C++ Makefile 專案

*Makefile* 是文字檔，其中包含如何編譯和連結 (或「建置」**) 一組 C++ 原始程式碼檔案的指示。 *Make* 程式會讀取 Makefile 並叫用編譯器、連結器和可能的其他程式來產生可執行檔。 Microsoft 對 *Make* 程式的實作稱為 [NMAKE](nmake-reference.md)。

如果您有現有的 Makefile 專案，則當您希望在 Visual Studio IDE 中撰寫和/或對其進行偵錯時，可以選擇這些選項：

- 在 Visual Studio 中建立 Makefile 專案，以使用現有 Makefile 來設定讓 Visual Studio 用於 IntelliSense 的 .vcxproj 檔案。  (您將不會擁有原生 MSBuild 專案所取得的所有 IDE 功能。 ) 請參閱 [，以在下方建立 makefile 專案](#create_a_makefile_project) 。
- 使用 [從現有程式碼檔建立新專案精靈]****，從您的原始程式碼建立原生 MSBuild 專案。 在此之後，將不再使用原始的 Makefile。 如需詳細資訊，請參閱[如何：從現有程式碼建立 C++ 專案](../how-to-create-a-cpp-project-from-existing-code.md)。
- **Visual Studio 2017 和更新版本**：使用 [ **開啟資料夾** ] 功能可依原樣編輯和建立 makefile 專案，而不會對 MSBuild 系統產生任何參與。 如需詳細資訊，請參閱 [Open Folder projects for C++](../open-folder-projects-cpp.md) (適用於 C++ 的開啟資料夾專案)。
- **Visual Studio 2019 和更新版本**：建立適用于 LINUX 的 UNIX makefile 專案。

## <a name="a-namecreate_a_makefile_project-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> 使用 Makefile 專案範本建立 Makefile 專案

在 Visual Studio 2017 和更新版本中，已安裝 C++ 桌面開發工作負載時，可以使用 Makefile 專案範本。

遵循精靈來指定 Makefile 所使用的命令和環境。 然後您就可以使用這個專案在 Visual Studio 中建置您的程式碼。

根據預設，Makefile 專案在 [方案總管] 中不會顯示任何檔案。 Makefile 專案指定的建置設定，會反映在專案的屬性頁中。

您在專案中指定的輸出檔案對建置指令碼產生的名稱沒有作用，它只是宣告一個意圖。 您的 Makefile 仍會控制建置程序並指定建置目標。

::: moniker range="vs-2019"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立 Makefile 專案

1. 從 Visual Studio 主功能表中 **，選擇 [** 檔案  >  **新增**  >  **專案**]，然後在 [搜尋] 方塊中輸入「makefile」。 或者，在 [新增專案]**** 對話方塊中，展開 [Visual C++]**** > [一般]**** (Visual Studio 2015) 或 [其他]**** (Visual Studio 2017)，然後根據您是以 Windows 或 Linux 為目標，來選擇兩個選項中的其中一個。

1. **僅限 Windows**：在 [ **debug Configuration 設定** ] 頁面中，提供 debug 和 retail 組建的命令、輸出、清除和重建資訊。 如果您想要指定不同的發行組態設定，請按 [下一步]****。

1. 按一下 [完成]**** 以關閉對話方塊，並在 [方案總管]**** 中開啟新建立的專案。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>在 Visual Studio 2015或 Visual Studio 2017 中建立 Makefile 專案

1. 在 Visual Studio 起始畫面的 [新增專案]**** 搜尋方塊中鍵入 "makefile"。 或者，在 [新增專案]**** 對話方塊中，展開 [Visual C++]**** > [一般]**** (Visual Studio 2015) 或 [其他]**** (Visual Studio 2017，然後選取 [範本] 窗格中的 [Makefile 專案]**** 以開啟專案精靈。

1. 在 **[應用程式設定]** 頁面中，提供偵錯和零售組建的命令、輸出、清除和重建資訊。

1. 按一下 [完成]**** 以關閉精靈並在 [方案總管]**** 中開啟新建立的專案。

::: moniker-end

您可以在屬性頁檢視和編輯專案的屬性。 請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)，以取得有關顯示屬性頁的資訊。

## <a name="makefile-project-wizard"></a>Makefile 專案精靈

建立 Makefile 專案之後，即可在專案屬性頁的 [Nmake]**** 頁面檢視和編輯下列每個選項。

- **組建命令列：** 指定當使用者從 [組建] 功能表選取 [建立] 時要執行的命令列。 顯示在專案屬性頁中 [Nmake] 頁面的 [建置命令列] 欄位。

- **輸出：** 指定將包含命令列輸出的檔案名。 根據預設，這個選項是根據專案名稱。 顯示在專案屬性頁中 [Nmake] 頁面的 [輸出] 欄位。

- **清除命令：** 指定當使用者從 [組建] 功能表選取 [清除] 時要執行的命令列。 顯示在專案屬性頁中 [Nmake] 頁面的 [清除命令列] 欄位。

- **重建命令列：** 指定當使用者從 [組建] 功能表選取 [重建] 時要執行的命令列。 顯示在專案屬性頁中 [Nmake] 頁面的 [全部重建命令列] 欄位。

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>如何：在 Makefile 專案中啟用 IntelliSense

不正確地設定某些專案設定或編譯器選項時，Makefile 專案中的 IntelliSense 會無法運作。 請遵循下列步驟來設定 Makefile 專案，讓 IntelliSense 可以正常運作：

1. 開啟 [屬性頁]**** 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性]**** 節點。

1. 選取 [NMake]**** 屬性頁，然後依適當情況修改 **IntelliSense** 下方屬性。

   - 設定 [前置處理器定義]**** 屬性，在 makefile 專案中定義任何前置處理器符號。 如需詳細資訊，請參閱 [/D (Preprocessor Definitions)](d-preprocessor-definitions.md)。

   - 設定 [包含搜尋路徑]**** 屬性，指定編譯器會搜尋的目錄清單，以便解析傳遞至 makefile 專案中之前置處理器指示詞的檔案參考。 如需詳細資訊，請參閱 [/I (其他 Include 目錄)](i-additional-include-directories.md)。

   - 對於使用 CL.EXE 從命令視窗建置的專案，設定 **INCLUDE** 環境變數，指定編譯器會搜尋的目錄清單，以便解析傳遞至 makefile 專案中之前置處理器指示詞的檔案參考。

   - 設定 [強制包含]**** 屬性，以指定在建置 makefile 專案時，要處理的標頭檔。 如需詳細資訊，請參閱 [/FI (指定強制的 Include 檔)](fi-name-forced-include-file.md)。

   - 設定 [組件搜尋路徑]**** 屬性，指定編譯器會搜尋的目錄清單，以便解析對您專案中 .NET 組件的參考。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](ai-specify-metadata-directories.md)。

   - 設定 [強制使用組件]**** 屬性，以指定在建置 makefile 專案時，要處理的 .NET 組件。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](fu-name-forced-hash-using-file.md)。

   - 設定 [ **其他選項** ] 屬性，以指定在剖析 c + + 檔案時，IntelliSense 所要使用的其他編譯器參數。

1. 按一下 [確定]**** 關閉屬性頁。

1. 使用 [全部儲存]**** 命令，儲存修改過的專案設定。

下次您在 Visual Studio 開發環境中開啟 makefile 專案，對您的 makefile 專案執行 [清除方案]**** 命令，然後執行 [建置方案]**** 命令。 IntelliSense 應該在 IDE 中正常運作。

## <a name="see-also"></a>另請參閱

[使用 IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE 參考](nmake-reference.md)<br>
[如何：從現有程式碼建立 C++ 專案](../how-to-create-a-cpp-project-from-existing-code.md)<br>
[Makefile 中的特殊字元](special-characters-in-a-makefile.md)<br/>
[Makefile 的內容](contents-of-a-makefile.md)<br/>
