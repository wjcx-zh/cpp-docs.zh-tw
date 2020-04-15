---
title: 編譯針對 CLR 的 C++/CLI 計劃
description: 使用 Microsoft C++創建可以連接本機 C++代碼和 .NET 程式的程式和庫。
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 0d661d9e77211a0e49f8695ad713b607377a236a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371817"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>演練:編譯面向視覺工作室中的 CLR 的C++/CLI 程式

通過使用C++/CLI,您可以創建C++程式,這些程式使用 .NET 類以及本機C++類型。 C++/CLI 用於控制台應用程式和 DLL 中,這些 DLL 包裝本機C++代碼,並可從 .NET 程式訪問它。 要基於 .NET 創建 Windows 使用者介面,請使用 C# 或可視化基本。

對於此過程,您可以鍵入自己的C++程式或使用其中一個示例程式。 我們在此程序中使用的範例程式會建立名為 textfile.txt 的文字檔，並將它儲存至專案目錄。

## <a name="prerequisites"></a>Prerequisites

- 對 C++ 語言基本知識的了解。
- 在 Visual Studio 2017 及更高版本中,C++/CLI 支援是可選元件。 要安裝它,請從「Windows」開始「選單開啟 **」 來檢視化工作室安裝程式**。 確保選取**了帶有C++磁貼的桌面開發**,並在 **「可選**元件」部分中,還檢查**C++/CLI 支援**。

## <a name="create-a-new-project"></a>建立新專案

下列步驟會依您使用的 Visual Studio 版本而略有不同。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>在 Visual Studio 2019 建立C++/CLI 專案

1. 在**解決方案資源管理器**中,右鍵單擊頂部以打開"**創建新專案**"對話方塊。

1. 在對話框的頂部,在搜尋框中鍵入**CLR,** 然後從結果清單中選擇**CLR 空專案**。

1. 選擇 [建立] **** 按鈕以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>在 Visual Studio 2017 建立C++/CLI 專案

1. 建立新專案。 在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。

1. 從 Visual C++ 專案類型，按一下 [CLR]****，然後按一下 [CLR 空專案]****。

1. 鍵入專案名稱。 根據預設，包含專案的方案與新專案具有相同的名稱，但您可以輸入不同的名稱。 如果您想要，也可以輸入不同的專案位置。

1. 按一下 [確定]**** 建立新專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>在 Visual Studio 2015 建立 C++/CLI 專案

1. 建立新專案。 在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。

1. 從 Visual C++ 專案類型，按一下 [CLR]****，然後按一下 [CLR 空專案]****。

1. 鍵入專案名稱。 根據預設，包含專案的方案與新專案具有相同的名稱，但您可以輸入不同的名稱。 如果您想要，也可以輸入不同的專案位置。

1. 按一下 [確定]**** 建立新專案。

::: moniker-end

## <a name="add-a-source-file"></a>新增來源

1. 如果未顯示 [方案總管]****，請按一下 [檢視]**** 功能表上的 [方案總管]****。

1. 新增原始程式檔至專案：

   - 右鍵按一下**解決方案資源管理員**中的**源檔案**資料夾,指向 **「添加**」,然後單擊 **「新專案**」。。

   - 按一下 [C++ 檔 (.cpp)]**** 並鍵入檔案名稱，然後按一下 [新增]****。

   **.cpp**檔將顯示在**解決方案資源管理員**中的**源檔案**資料夾中,並在其中鍵入所需的代碼的位置顯示一個選項卡式視窗。

1. 按一下 Visual Studio 中新建立的索引標籤，然後鍵入有效的 Visual C++ 程式，或複製並貼上其中一個範例程式。

   例如，您可以使用[如何：寫入文字檔 (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) 範例程式 (位於《程式設計指南》的**檔案處理和 I/O**節點中)。

   如果您使用範例程式，注意您會在建立 .NET 物件時使用 `gcnew` 關鍵字而不是 `new`，而且 `gcnew` 會傳回控制代碼 (`^`) 而不是指標 (`*`)：

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   有關C++/CLI 語法的詳細資訊,請參閱[執行時平臺的元件擴展](../extensions/component-extensions-for-runtime-platforms.md)。

1. 在 [建置]**** 功能表上，按一下 [建置方案]****。

   [輸出]**** 視窗會顯示編譯進度的相關資訊，例如組建記錄檔的位置，以及指出組建狀態的訊息。

   如果您進行變更，然後執行程式而不進行建置，對話方塊可能會指出專案已過期。 如果您想要 Visual Studio 一律使用目前版本的檔案，而不是每次建置應用程式都提示您，請先選取此對話方塊上的核取方塊，再按一下 [確定]****。

1. 在 [偵錯]**** 功能表上，按一下 [啟動但不偵錯]****。

1. 如果您使用範例程式，當您執行程式時，就會顯示命令視窗指出已建立文字檔。

   **textfile.txt** 文字檔現在位於專案目錄中。 您可以使用 [記事本] 開啟此檔案。

   > [!NOTE]
   > 選擇空白的 CLR 專案範本時，會自動設定 `/clr` 編譯器選項。 若要進行確認，請以滑鼠右鍵按一下 [方案總管]**** 中的專案並按一下 [屬性]****，然後在 [組態屬性]**** 的 [一般]**** 節點中，核取 [Common Language Runtime 支援]****。

## <a name="see-also"></a>另請參閱

[C++語言參考](../cpp/cpp-language-reference.md)<br/>
[專案和建置系統](../build/projects-and-build-systems-cpp.md)<br/>
