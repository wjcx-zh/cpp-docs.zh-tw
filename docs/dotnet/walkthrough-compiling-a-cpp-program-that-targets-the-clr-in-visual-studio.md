---
title: 編譯以 CLR 為目標的 c + +/CLI 程式
description: 使用 Microsoft c + + 建立可連接原生 c + + 程式碼和 .NET 程式的程式和程式庫。
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 2fceb57e062b9179245ba235fb497ff526a6660e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501678"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>逐步解說：在 Visual Studio 中編譯以 CLR 為目標的 c + +/CLI 程式

您可以使用 c + +/CLI 來建立 c + + 程式，以使用 .NET 類別和原生 c + + 類型。 C + +/CLI 適用于主控台應用程式，以及包裝原生 c + + 程式碼並可從 .NET 程式存取的 Dll 中。 若要建立以 .NET 為基礎的 Windows 使用者介面，請使用 c # 或 Visual Basic。

針對此程式，您可以輸入自己的 c + + 程式，或使用其中一個範例程式。 我們在此程序中使用的範例程式會建立名為 textfile.txt 的文字檔，並將它儲存至專案目錄。

## <a name="prerequisites"></a>必要條件

- 對 C++ 語言基本知識的了解。
- 在 Visual Studio 2017 和更新版本中，c + +/CLI 支援是選擇性元件。 若要安裝它，請從 Windows [開始] 功能表開啟 **Visual Studio 安裝程式** 。 確定已核取 [ **使用 c + + 進行桌面開發** ] 磚，並在 [ **選用** 元件] 區段中，檢查 **c + +/cli 支援**。

## <a name="create-a-new-project"></a>建立新專案

下列步驟會依您使用的 Visual Studio 版本而略有不同。 若要查看您慣用 Visual Studio 版本的檔，請使用 **版本** 選擇器控制項。 您可在此頁面的目錄頂端找到此檔案。

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立 c + +/CLI 專案

1. 在 **方案總管**中，以滑鼠右鍵按一下頂端以開啟 [ **建立新專案** ] 對話方塊。

1. 在對話方塊頂端的 [搜尋] 方塊中輸入 **clr** ，然後從結果清單中選擇 [ **clr 空專案** ]。

1. 選擇 [建立] **** 按鈕以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>若要在 Visual Studio 2017 中建立 c + +/CLI 專案

1. 建立新專案。 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

1. 從 Visual C++ 專案類型，按一下 [CLR]****，然後按一下 [CLR 空專案]****。

1. 鍵入專案名稱。 根據預設，包含專案的方案與新專案具有相同的名稱，但您可以輸入不同的名稱。 如果您想要，也可以輸入不同的專案位置。

1. 按一下 [確定]**** 建立新專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中建立 c + +/CLI 專案

1. 建立新專案。 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

1. 從 Visual C++ 專案類型，按一下 [CLR]****，然後按一下 [CLR 空專案]****。

1. 鍵入專案名稱。 根據預設，包含專案的方案與新專案具有相同的名稱，但您可以輸入不同的名稱。 如果您想要，也可以輸入不同的專案位置。

1. 按一下 [確定]**** 建立新專案。

::: moniker-end

## <a name="add-a-source-file"></a>新增原始檔

1. 如果未顯示 [方案總管]****，請按一下 [檢視]**** 功能表上的 [方案總管]****。

1. 新增原始程式檔至專案：

   - 以滑鼠右鍵按一下**方案總管**中的 [**來源**檔案] 資料夾，指向 [**加入**]，然後按一下 [**新增專案**]。

   - 按一下 [C++ 檔 (.cpp)]**** 並鍵入檔案名稱，然後按一下 [新增]****。

   **.Cpp**檔會出現在**方案總管**的 [**原始**程式檔] 資料夾中，而且會出現索引標籤式視窗，讓您在該檔案中輸入想要的程式碼。

1. 按一下 Visual Studio 中新建立的索引標籤，然後鍵入有效的 Visual C++ 程式，或複製並貼上其中一個範例程式。

   例如，您可以使用[如何：寫入文字檔 (C++/CLI)](./file-handling-and-i-o-cpp-cli.md#write_text) 範例程式 (位於《程式設計指南》的**檔案處理和 I/O**節點中)。

   如果您使用範例程式，請注意， **`gcnew`** 當您建立 .net 物件時，會使用關鍵字而不是，而 **`new`** 會傳回 **`gcnew`** 控制碼 (`^`) 而非指標 (`*`) ：

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   如需 c + +/CLI 語法的詳細資訊，請參閱 [執行時間平臺的元件擴充](../extensions/component-extensions-for-runtime-platforms.md)功能。

1. 在 [建置] 功能表上，按一下 [建置方案]。

   [輸出]**** 視窗會顯示編譯進度的相關資訊，例如組建記錄檔的位置，以及指出組建狀態的訊息。

   如果您進行變更，然後執行程式而不進行建置，對話方塊可能會指出專案已過期。 如果您想要 Visual Studio 一律使用目前版本的檔案，而不是每次建置應用程式都提示您，請先選取此對話方塊上的核取方塊，再按一下 [確定]****。

1. 在 [偵錯]**** 功能表上，按一下 [啟動但不偵錯]****。

1. 如果您使用範例程式，當您執行程式時，就會顯示命令視窗指出已建立文字檔。

   **textfile.txt** 文字檔現在位於專案目錄中。 您可以使用 [記事本] 開啟此檔案。

   > [!NOTE]
   > 選擇空白的 CLR 專案範本時，會自動設定 `/clr` 編譯器選項。 若要進行確認，請以滑鼠右鍵按一下 [方案總管]**** 中的專案並按一下 [屬性]****，然後在 [組態屬性]**** 的 [一般]**** 節點中，核取 [Common Language Runtime 支援]****。

## <a name="see-also"></a>另請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[專案與建置系統](../build/projects-and-build-systems-cpp.md)<br/>
