---
title: 逐步解說：建立標準 C++ 程式 (C++)
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 105ac62131b45afdea2a445b5888a344f1e4d46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370230"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>逐步解說：建立標準 C++ 程式 (C++)

您可以使用可視化工作室創建標準C++程式。 以按照本演練中的步驟,您可以創建專案、向專案添加新檔、修改檔以添加C++代碼,然後使用 Visual Studio 編譯和運行程式。

您可以鍵入自己的C++程式或使用其中一個範例程式。 本演練中的範例程式是主控台應用程式。 此應用程式使用標準`set`庫中的容器C++。

> [!NOTE]
> 如果需要符合C++語言標準的特定版本(即C++14 或C++17),請使用`/std:c++14``/std:c++17`或編譯器選項。 (視覺工作室 2017 及更高版本。

## <a name="prerequisites"></a>Prerequisites

若要完成此逐步解說，您必須了解 C++ 語言的基礎。

### <a name="to-create-a-project-and-add-a-source-file"></a>建立專案並新增來源

下列步驟會依您使用的 Visual Studio 版本而略有不同。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>在視覺工作室 2019 中創建C++專案

1. 從主功能表，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**主控台**。

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]****，然後選擇 [下一步]****。 在下一頁中,輸入專案的名稱,並根據需要指定專案位置。

1. 選擇 [建立] **** 按鈕以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>在視覺工作室 2017 中創建C++專案

1. 以指向 **「檔案**」功能表上的 **「新建**」,然後單擊 **「專案**」,創建專案。

1. 在 **「視覺C++** 專案類型窗格中,按**下 Windows 桌面**」,然後按**下 Windows 主控台應用程式**。

1. 鍵入專案的名稱。 預設情況下,包含專案的解決方案的名稱與專案相同,但可以鍵入其他名稱。 您還可以為項目鍵入其他位置。

1. 按一下 [確定]**** 建立專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>在視覺工作室 2015 中創建C++專案

1. 以指向 **「檔案**」功能表上的 **「新建**」,然後單擊 **「專案**」,創建專案。

1. 在 **「視覺C++** 專案類型窗格中,按**下 Windows 桌面**」,然後按**下 Windows 主控台應用程式**。

1. 在 **「新項目**」 對話框中,展開 **「已安裝** > **樣本** > **」可視C++,** 然後選擇**Win32**。 在中央窗格中，選取 [Win32 主控台應用程式] ****。

1. 鍵入專案的名稱。 預設情況下,包含專案的解決方案的名稱與專案相同,但可以鍵入其他名稱。 您還可以為項目鍵入其他位置。

1. 按一下 [確定]**** 建立專案。

1. 完成**Win32 應用程式精靈**。

1. 按下 **「下一步**」,然後確保選擇**主控台應用程式**並取消選中 **「預編譯標頭」** 框。

1. 按一下 [完成] 。

::: moniker-end

## <a name="add-a-new-source-file"></a>新增來源檔案

1. 如果未顯示**解決方案資源管理員**,請在 **「檢視」** 功能表上單擊 **「解決方案資源管理器**」。

1. 向專案添加新源檔,如下所示。

   1. 在 **「解決方案資源管理員」** 中,右鍵按**下 「源檔」** 資料夾,指向 **「添加**」,然後單擊 **「新專案**」。

   1. 在 **「代碼」** 節點中,按下**C++檔 (.cpp)**,鍵入檔案的名稱,然後按一下「**添加**」。

   .cpp 檔案將顯示在**解決方案資源管理員**中的**源檔案**資料夾中,該檔在 Visual Studio 編輯器中打開。

1. 在編輯器中的檔中,鍵入使用C++標準庫的有效C++程式,或複製其中一個示例程式並將其貼貼到檔中。

1. 儲存檔案。

1. 在 [建置]**** 功能表上，按一下 [建置方案]****。

   輸出 **「** 視窗顯示有關編譯進度的資訊,例如,生成日誌的位置和指示生成狀態的消息。

1. 在 [偵錯]**** 功能表上，按一下 [啟動但不偵錯]****。

   如果使用範例程式,將顯示一個命令視窗,並顯示在集中是否找到某些整數。

## <a name="next-steps"></a>後續步驟

**上一個:**[視覺C++中的主控台應用程式](../windows/console-applications-in-visual-cpp.md)<br/>
**下一頁:**[演練:在命令列上編譯本機C++程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>另請參閱

[C++語言參考](../cpp/cpp-language-reference.md)<br/>
[C++標準庫](../standard-library/cpp-standard-library-reference.md)
