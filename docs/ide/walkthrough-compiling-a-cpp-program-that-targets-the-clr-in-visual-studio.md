---
title: 編譯針對 CLR 的 C++ 程式 | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c656f2f11de6b33ae7299215192a2bbb8750c53d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078735"
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>逐步解說：編譯針對 Visual Studio 中 CLR 的 C++ 程式

您可以建立使用 .NET 類別的 Visual C++ 程式，並使用 Visual Studio 開發環境進行編譯。

在此程序中，您可以鍵入自己的 Visual C++ 程式，或使用其中一個範例程式。 我們在此程序中使用的範例程式會建立名為 textfile.txt 的文字檔，並將它儲存至專案目錄。

## <a name="prerequisites"></a>必要條件

這些主題假設您已了解 C++ 語言的基本概念。

### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>在 Visual Studio 中建立新專案並新增原始程式檔

1. 建立新的專案。 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

1. 從 Visual C++ 專案類型，按一下 [CLR]，然後按一下 [CLR 空專案]。

   > [!NOTE]
   > 如果遺漏 [CLR 空專案] 類型 (僅限 Visual Studio 2017)，請選取 [新增專案] 對話方塊左窗格中的 [開啟 Visual Studio 安裝程式]。 安裝位於 [選用元件] 區段中 [使用 C++ 的桌面開發] 下方的選項 ，其名稱為 [C++/CLI 支援]。<br/>

1. 鍵入專案名稱。

    根據預設，包含專案的方案與新專案具有相同的名稱，但您可以輸入不同的名稱。 如果您想要，也可以輸入不同的專案位置。

    按一下 [確定] 建立新專案。

1. 如果未顯示 [方案總管]，請按一下 [檢視] 功能表上的 [方案總管]。

1. 新增原始程式檔至專案：

    - 以滑鼠右鍵按一下 [方案總管] 中的**來源檔案**資料夾，指向 [新增]，然後按一下 [新增項目]。

    - 按一下 [C++ 檔 (.cpp)] 並鍵入檔案名稱，然後按一下 [新增]。

    **.cpp** 檔案會出現在 [方案總管] 的**來源檔案**資料夾中；當您在該檔案中鍵入所需程式碼時，該處會顯示索引標籤式視窗。

1. 按一下 Visual Studio 中新建立的索引標籤，然後鍵入有效的 Visual C++ 程式，或複製並貼上其中一個範例程式。

    例如，您可以使用[如何：寫入文字檔 (C++/CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) 範例程式 (位於《程式設計指南》的**檔案處理和 I/O**節點中)。

    如果您使用範例程式，注意您會在建立 .NET 物件時使用 `gcnew` 關鍵字而不是 `new`，而且 `gcnew` 會傳回控制代碼 (`^`) 而不是指標 (`*`)：

    `StreamWriter^ sw = gcnew StreamWriter(fileName);`

    如需新 Visual C++ 語法的詳細資訊，請參閱[執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)。

1. 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

    [輸出] 視窗會顯示編譯進度的相關資訊，例如組建記錄檔的位置，以及指出組建狀態的訊息。

    如果您進行變更，然後執行程式而不進行建置，對話方塊可能會指出專案已過期。 如果您想要 Visual Studio 一律使用目前版本的檔案，而不是每次建置應用程式都提示您，請先選取此對話方塊上的核取方塊，再按一下 [確定]。

1. 在 [偵錯] 功能表上，按一下 [啟動但不偵錯]。

1. 如果您使用範例程式，當您執行程式時，就會顯示命令視窗指出已建立文字檔。

    **textfile.txt** 文字檔現在位於專案目錄中。 您可以使用 [記事本] 開啟此檔案。

    > [!NOTE]
    > 選擇空白的 CLR 專案範本時，會自動設定 `/clr` 編譯器選項。 若要進行確認，請以滑鼠右鍵按一下 [方案總管] 中的專案並按一下 [屬性]，然後在 [組態屬性] 的 [一般] 節點中，核取 [Common Language Runtime 支援]。

## <a name="whats-next"></a>後續步驟

**上一個主題：**[逐步解說：在命令列上編譯原生 C++ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
**下一個主題：**[逐步解說：在命令列上編譯 C 程式](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[建置 C/C++ 程式](../build/building-c-cpp-programs.md)<br/>
