---
title: 編譯C++CLR 為目標的 /CLI 程式
description: 使用 MicrosoftC++來建立程式和程式庫，可以連接的原生C++程式碼及.NET 程式。
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 8462b2b031bdcdebf65d58974c521d80e57d856d
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221802"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>逐步解說：編譯C++Visual Studio 中 Clr 的 /CLI 程式

使用C++您可以建立 CLI/C++使用.NET 類別，以及原生的程式C++類型。 C++/ CLI 適用於在主控台應用程式和 Dll 包裝原生C++程式碼，並使它成為可從.NET 程式存取。 若要建立.NET 為基礎的 Windows 使用者介面，請使用C#或 Visual Basic。 

此程序中，您可以輸入自己C++程式，或使用其中一個範例程式。 我們在此程序中使用的範例程式會建立名為 textfile.txt 的文字檔，並將它儲存至專案目錄。

## <a name="prerequisites"></a>必要條件

- 對 C++ 語言基本知識的了解。
- 在 Visual Studio 2017 和更新版本， C++/CLI 支援是選擇性元件。 若要安裝，請開啟**Visual Studio 安裝程式**從 Windows [開始] 功能表。 請確定**使用的桌面開發C++** 勾選 圖格，然後在**選擇性**元件 區段中，也檢查 **C++CLI 支援**。

## <a name="create-a-new-project"></a>建立新專案

下列步驟，視您所使用的 Visual Studio 版本而有所不同。 請確定版本中的選取器的右上方的此頁面已正確設定。

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>若要建立C++在 Visual Studio 2019 /CLI 專案

1. 中**方案總管**，以滑鼠右鍵按一下以開啟頂端**建立新的專案**對話方塊。

1. 在對話方塊頂端，輸入**CLR**在搜尋 方塊，然後選擇**CLR 空專案**從結果清單中。 

1. 選擇**建立**按鈕，以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>若要建立C++Visual Studio 2017 中的 /CLI 專案

1. 建立新的專案。 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

1. 從 Visual C++ 專案類型，按一下 [CLR]，然後按一下 [CLR 空專案]。

1. 鍵入專案名稱。 根據預設，包含專案的方案與新專案具有相同的名稱，但您可以輸入不同的名稱。 如果您想要，也可以輸入不同的專案位置。

1. 按一下 [確定] 建立新專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>若要建立C++在 Visual Studio 2015 的 /CLI 專案

1. 建立新的專案。 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

1. 從 Visual C++ 專案類型，按一下 [CLR]，然後按一下 [CLR 空專案]。

1. 鍵入專案名稱。 根據預設，包含專案的方案與新專案具有相同的名稱，但您可以輸入不同的名稱。 如果您想要，也可以輸入不同的專案位置。

1. 按一下 [確定] 建立新專案。

::: moniker-end

## <a name="add-a-source-file"></a>加入原始程式檔

1. 如果未顯示 [方案總管]，請按一下 [檢視] 功能表上的 [方案總管]。

1. 新增原始程式檔至專案：

   - 以滑鼠右鍵按一下 [方案總管] 中的**來源檔案**資料夾，指向 [新增]，然後按一下 [新增項目]。

   - 按一下 [C++ 檔 (.cpp)] 並鍵入檔案名稱，然後按一下 [新增]。

   **.cpp** 檔案會出現在 [方案總管] 的**來源檔案**資料夾中；當您在該檔案中鍵入所需程式碼時，該處會顯示索引標籤式視窗。

1. 按一下 Visual Studio 中新建立的索引標籤，然後鍵入有效的 Visual C++ 程式，或複製並貼上其中一個範例程式。

   例如，您可以使用[如何：撰寫文字檔 (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) 範例程式 (位於《程式設計指南》的**檔案處理和 I/O** 節點中)。

   如果您使用範例程式，注意您會在建立 .NET 物件時使用 `gcnew` 關鍵字而不是 `new`，而且 `gcnew` 會傳回控制代碼 (`^`) 而不是指標 (`*`)：

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   如需詳細資訊C++/CLI 語法，請參閱[執行階段平台的元件延伸模組](../extensions/component-extensions-for-runtime-platforms.md)。

1. 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   [輸出] 視窗會顯示編譯進度的相關資訊，例如組建記錄檔的位置，以及指出組建狀態的訊息。

   如果您進行變更，然後執行程式而不進行建置，對話方塊可能會指出專案已過期。 如果您想要 Visual Studio 一律使用目前版本的檔案，而不是每次建置應用程式都提示您，請先選取此對話方塊上的核取方塊，再按一下 [確定]。

1. 在 [偵錯] 功能表上，按一下 [啟動但不偵錯]。

1. 如果您使用範例程式，當您執行程式時，就會顯示命令視窗指出已建立文字檔。

   **textfile.txt** 文字檔現在位於專案目錄中。 您可以使用 [記事本] 開啟此檔案。

   > [!NOTE]
   > 選擇空白的 CLR 專案範本時，會自動設定 `/clr` 編譯器選項。 若要進行確認，請以滑鼠右鍵按一下 [方案總管] 中的專案並按一下 [屬性]，然後在 [組態屬性] 的 [一般] 節點中，核取 [Common Language Runtime 支援]。

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[專案和建置系統](../build/projects-and-build-systems-cpp.md)<br/>
