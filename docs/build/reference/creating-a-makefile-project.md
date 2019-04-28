---
title: 建立C++Visual Studio 中的 makefile 專案
ms.date: 12/08/2018
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: 9c2edfe35233672e8117d336ba40cfea497b1a22
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272343"
---
# <a name="create-a-c-makefile-project"></a>建立C++makefile 專案

*Makefile* 是文字檔，其中包含如何編譯和連結 (或「建置」) 一組 C++ 原始程式碼檔案的指示。 *Make* 程式會讀取 Makefile 並叫用編譯器、連結器和可能的其他程式來產生可執行檔。 Microsoft 的實作*製作*程式稱為 「 [NMAKE](nmake-reference.md);

如果您有現有的 Makefile 專案，則當您希望在 Visual Studio IDE 中撰寫和/或對其進行偵錯時，可以選擇這些選項：

- 若要設定 Visual Studio 會使用適用於 IntelliSense 的.vcxproj 檔案會使用您現有 makefile 的 Visual Studio 中建立一個 makefile 專案。 (您將無法使用原生 MSBuild 專案取得所有 IDE 功能。)請參閱下方的[建立 Makefile 專案](#create_a_makefile_project)。
- 使用 [從現有程式碼檔建立新專案精靈]，從您的原始程式碼建立原生 MSBuild 專案。 在此之後，不會使用原始的 makefile。 如需詳細資訊，請參閱[如何：從現有的程式碼建立 C++ 專案](../how-to-create-a-cpp-project-from-existing-code.md)。
- **Visual Studio 2017 及更新版本**：使用**開啟資料夾**編輯和建置 makefile 專案做為功能-是不需要任何涉入 MSBuild 系統。 如需詳細資訊，請參閱 [Open Folder projects for C++](../open-folder-projects-cpp.md) (適用於 C++ 的開啟資料夾專案)。

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> Makefile 專案範本建立 makefile 專案

在 Visual Studio 2017 和更新版本中，已安裝 C++ 桌面開發工作負載時，可以使用 Makefile 專案範本。

遵循精靈來指定 Makefile 所使用的命令和環境。 您接著可以使用這個專案來建置您的程式碼，在 Visual Studio 中。

根據預設，Makefile 專案在 [方案總管] 中不會顯示任何檔案。 Makefile 專案指定的建置設定，會反映在專案的屬性頁中。

您在專案中指定的輸出檔案對建置指令碼產生的名稱沒有作用，它只是宣告一個意圖。 您的 Makefile 仍會控制建置程序並指定建置目標。

1. 在 Visual Studio 起始畫面的 [新增專案] 搜尋方塊中鍵入 "makefile"。 或者，在 [新增專案] 對話方塊中，展開 [Visual C++] > [一般] (Visual Studio 2015) 或 [其他] (Visual Studio 2017，然後選取 [範本] 窗格中的 [Makefile 專案] 以開啟專案精靈。

1. 在 **[應用程式設定]** 頁面中，提供偵錯和零售組建的命令、輸出、清除和重建資訊。

1. 按一下 [完成] 以關閉精靈並在 [方案總管] 中開啟新建立的專案。

您可以在屬性頁檢視和編輯專案的屬性。 請參閱[設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)如需有關顯示屬性頁資訊。

## <a name="makefile-project-wizard"></a>Makefile 專案精靈

建立 makefile 專案之後，您可以檢視並編輯下列選項中的每個**Nmake**專案的 [屬性] 頁面的頁面。

- **建置命令列：** 指定當使用者從 建置 功能表中選取 建置時要執行的命令列。 顯示在專案的屬性頁的 Nmake 頁面上的建置命令列 欄位中。

- **輸出：** 指定將包含命令列輸出之檔案的名稱。 根據預設，這個選項是根據專案名稱。 顯示在專案的屬性頁的 Nmake 頁面上的 [輸出] 欄位。

- **全新的命令：** 指定當使用者從 建置 功能表中選取 清除時要執行的命令列。 顯示在專案的屬性頁的 Nmake 頁面上的 [清除命令列] 欄位中。

- **重建命令列：** 指定當使用者從 建置 功能表中選取 重建時要執行的命令列。 在重建所有的命令列欄位 Nmake 的頁面上顯示專案的屬性頁。

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>HOW TO：啟用 Makefile 專案的 IntelliSense

某些專案設定] 或 [編譯器選項會設定不正確時，IntelliSense 會無法在 makefile 專案中。 請遵循下列步驟來設定 makefile 專案，讓 IntelliSense 可以正常運作：

1. 開啟 [屬性頁] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 展開 [組態屬性] 節點。

1. 選取 [NMake] 屬性頁，然後依適當情況修改 **IntelliSense** 下方屬性。

   - 設定 [前置處理器定義] 屬性，在 makefile 專案中定義任何前置處理器符號。 如需詳細資訊，請參閱 [/D (Preprocessor Definitions)](d-preprocessor-definitions.md)。

   - 設定 [包含搜尋路徑] 屬性，指定編譯器會搜尋的目錄清單，以便解析傳遞至 makefile 專案中之前置處理器指示詞的檔案參考。 如需詳細資訊，請參閱 [/I (其他 Include 目錄)](i-additional-include-directories.md)。

    - 對於使用 CL.EXE 從命令視窗建置的專案，設定 **INCLUDE** 環境變數，指定編譯器會搜尋的目錄清單，以便解析傳遞至 makefile 專案中之前置處理器指示詞的檔案參考。

   - 設定 [強制包含] 屬性，以指定在建置 makefile 專案時，要處理的標頭檔。 如需詳細資訊，請參閱 [/FI (指定強制的 Include 檔)](fi-name-forced-include-file.md)。

   - 設定 [組件搜尋路徑] 屬性，指定編譯器會搜尋的目錄清單，以便解析對您專案中 .NET 組件的參考。 如需詳細資訊，請參閱 [/AI (指定中繼資料目錄)](ai-specify-metadata-directories.md)。

   - 設定 [強制使用組件] 屬性，以指定在建置 makefile 專案時，要處理的 .NET 組件。 如需詳細資訊，請參閱 [/FU (指定強制的 #using 檔)](fu-name-forced-hash-using-file.md)。

   - 設定 [其他選項] 屬性，指定在剖析 C++ 檔案時，IntelliSense 要使用的其他編譯器參數。

1. 按一下 [確定] 關閉屬性頁。

1. 使用 [全部儲存] 命令，儲存修改過的專案設定。

下次您在 Visual Studio 開發環境中開啟 makefile 專案，對您的 makefile 專案執行 [清除方案] 命令，然後執行 [建置方案] 命令。 IntelliSense 應該在 IDE 中正常運作。

## <a name="see-also"></a>另請參閱

[使用 IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE 參考](nmake-reference.md)<br>
[如何：建立C++從現有的程式碼專案](../how-to-create-a-cpp-project-from-existing-code.md)
[Makefile 中的特殊字元](special-characters-in-a-makefile.md)<br/>
[Makefile 內容](contents-of-a-makefile.md)<br/>
