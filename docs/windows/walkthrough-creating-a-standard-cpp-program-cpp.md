---
title: 逐步解說：建立標準 C++ 程式 (C++)
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: bf2a3fac92b756b395eda236ed4968608319823c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509607"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>逐步解說：建立標準 C++ 程式 (C++)

您可以使用 Visual Studio 建立標準 c + + 程式。 藉由遵循本逐步解說中的步驟，您可以建立專案、將新檔案加入至專案、修改檔案以加入 c + + 程式碼，然後使用 Visual Studio 來編譯和執行程式。

您可以輸入自己的 c + + 程式，或使用其中一個範例程式。 本逐步解說中的範例程式是主控台應用程式。 此應用程式會使用 `set` c + + 標準程式庫中的容器。

> [!NOTE]
> 如果符合特定版本的 c + + 語言標準 (即需要 c + + 14 或 c + + 17) ，請使用 `/std:c++14` 或 `/std:c++17` 編譯器選項。  (Visual Studio 2017 和更新版本。 ) 

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您必須了解 C++ 語言的基礎。

### <a name="to-create-a-project-and-add-a-source-file"></a>若要建立專案並新增原始檔

下列步驟會依您使用的 Visual Studio 版本而略有不同。 若要查看您慣用 Visual Studio 版本的檔，請使用 **版本** 選擇器控制項。 您可在此頁面的目錄頂端找到此檔案。

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立 c + + 專案

1. 從主功能表，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**主控台**。

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]****，然後選擇 [下一步]****。 在下一個頁面中，輸入專案的名稱，並視需要指定專案位置。

1. 選擇 [建立] **** 按鈕以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>若要在 Visual Studio 2017 中建立 c + + 專案

1. **在 [檔案**] 功能表上指向 [**新增**]，然後按一下 [**專案**]，以建立專案。

1. 在 [ **Visual C++** 專案類型] 窗格中，按一下 [ **windows 桌面**]，然後按一下 [ **windows 主控台應用程式**]。

1. 輸入專案的名稱。 依預設，包含專案的方案與專案的名稱相同，但您可以輸入不同的名稱。 您也可以輸入不同的專案位置。

1. 按一下 [確定]  以建立專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中建立 c + + 專案

1. **在 [檔案**] 功能表上指向 [**新增**]，然後按一下 [**專案**]，以建立專案。

1. 在 [ **Visual C++** 專案類型] 窗格中，按一下 [ **windows 桌面**]，然後按一下 [ **windows 主控台應用程式**]。

1. 在 [**新增專案**] 對話方塊中，展開 [**已安裝**  >  的**範本**]  >  **Visual C++**，然後選取 [ **Win32**]。 在中央窗格中，選取 [Win32 主控台應用程式] ****。

1. 輸入專案的名稱。 依預設，包含專案的方案與專案的名稱相同，但您可以輸入不同的名稱。 您也可以輸入不同的專案位置。

1. 按一下 [確定]  以建立專案。

1. 完成 **Win32 應用程式精靈**。

1. 按 **[下一步]**，確定已選取 [ **主控台應用程式** ]，並取消選取 [先行 **編譯頭** 檔] 方塊

1. 按一下 [完成] 。

::: moniker-end

## <a name="add-a-new-source-file"></a>新增原始檔

1. 如果未顯示 **方案總管** ，請按一下 [ **View** ] 功能表上的 [ **方案總管**]。

1. 將新的原始檔新增至專案，如下所示。

   1. 在 **方案總管**中，以滑鼠右鍵按一下 [ **來源** 檔案] 資料夾，指向 [ **加入**]，然後按一下 [ **新增專案**]。

   1. 在 [程式 **代碼** ] 節點中，按一下 [ **c + + 檔案 ( .cpp) **，輸入檔案的名稱，然後按一下 [ **新增**]。

   .Cpp 檔會出現在**方案總管**的 [**原始**程式檔] 資料夾中，並在 Visual Studio 編輯器中開啟該檔案。

1. 在編輯器的檔案中，輸入使用 c + + 標準程式庫的有效 c + + 程式，或複製其中一個範例程式，並將它貼入檔案中。

1. 儲存檔案。

1. 在 [建置] 功能表上，按一下 [建置方案]。

   [ **輸出** ] 視窗會顯示編譯進度的相關資訊，例如組建記錄檔的位置，以及指出組建狀態的訊息。

1. 在 [偵錯]**** 功能表上，按一下 [啟動但不偵錯]****。

   如果您使用範例程式，則會顯示命令視窗，並顯示是否在集合中找到特定的整數。

## <a name="next-steps"></a>後續步驟

**上一個：** [Visual C++ 中的主控台應用程式](./overview-of-windows-programming-in-cpp.md)<br/>
**下一步：** [逐步解說：在命令列上編譯原生 c + + 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>另請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
