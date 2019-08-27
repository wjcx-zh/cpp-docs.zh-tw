---
title: 逐步解說：建立標準C++程式 (C++)
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: b3172dd6ed4c438bacedd6760da5ab65228396f3
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400913"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>逐步解說：建立標準C++程式 (C++)

您可以使用 Visual Studio 來建立標準C++程式。 依照本逐步解說中的步驟，建立專案、 將新檔案新增至專案、 修改檔案以新增C++程式碼，然後編譯及執行使用 Visual Studio 的程式。

您也可以輸入自己C++程式，或使用其中一個範例程式。 在本逐步解說的範例程式是主控台應用程式。 此應用程式會使用`set`容器中的C++標準程式庫。

> [!NOTE]
> 如果符合特定版本的C++語言標準 （也就是 C + + 14 或 C + + 17） 時，使用`/std:C++14`或是`/std:c++17`編譯器選項。 (Visual Studio 2017 和更新版本。)

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您必須了解 C++ 語言的基礎。

### <a name="to-create-a-project-and-add-a-source-file"></a>若要建立專案並加入原始程式檔

下列步驟會依您使用的 Visual Studio 版本而略有不同。 請確認本頁面左上角的版本選取器已正確設定。

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>若要建立C++在 Visual Studio 2019 的專案

1. 從主功能表，選擇 [檔案]  > [新增]  > [專案]  ，以開啟 [建立新專案]  對話方塊。

1. 在對話方塊頂端，將 [語言]  設定為 **C++** ，將 [平台]  設定為 **Windows**，並將 [專案類型]  設定為**主控台**。 

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]  ，然後選擇 [下一步]  。 在下一步 頁面中，輸入專案名稱，然後指定專案位置，如有需要。

1. 選擇 [建立]  按鈕以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>若要建立C++Visual Studio 2017 中的專案

1. 建立專案，指向**的新**上**檔案**功能表，然後按一下**專案**。

1. 在  **Visual C++** 專案類型 窗格中，按一下  **Windows 桌面**，然後按一下**Windows 主控台應用程式**。

1. 輸入專案的名稱。 根據預設，包含專案的方案具有相同的名稱，為專案，但您可以輸入不同的名稱。 您也可以輸入專案的不同位置。

1. 按一下 [確定]  建立專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>若要建立C++Visual Studio 2015 中的專案

1. 建立專案，指向**的新**上**檔案**功能表，然後按一下**專案**。

1. 在  **Visual C++** 專案類型 窗格中，按一下  **Windows 桌面**，然後按一下**Windows 主控台應用程式**。

1. 在 **新的專案**對話方塊方塊中，展開**已安裝** > **範本** > **Visual C++** ，和然後選取**Win32**。 在中央窗格中，選取 [Win32 主控台應用程式]  。

1. 輸入專案的名稱。 根據預設，包含專案的方案具有相同的名稱，為專案，但您可以輸入不同的名稱。 您也可以輸入專案的不同位置。

1. 按一下 [確定]  建立專案。

1. 完成**Win32 應用程式精靈**。 

1. 按一下 [**下一步**，然後確定**主控台應用程式**已選取，並取消核取**先行編譯標頭**] 方塊中。 

1. 按一下 [ **完成**]。

::: moniker-end

## <a name="add-a-new-source-file"></a>加入新的原始程式檔

1. 如果**方案總管**未顯示，請在**檢視**功能表上，按一下 [**方案總管] 中**。

1. 將新的原始程式檔，如下所示新增至專案。

   1. 中**方案總管**，以滑鼠右鍵按一下**原始程式檔**資料夾，指向**新增**，然後按一下**新項目**。

   1. 在 **程式碼**節點，按一下**C++檔 (.cpp)** ，輸入檔案的名稱，然後按一下**新增**。

   .Cpp 檔案中會出現在**原始程式檔**中的資料夾**方案總管 中**，和 Visual Studio 編輯器中開啟檔案。

1. 在檔案中在編輯器中，輸入有效的C++程式，使用C++標準程式庫或複製其中一個範例程式，並將它貼在檔案中。

1. 儲存檔案。

1. 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   **輸出**視窗會顯示有關編譯進度，比方說，建置記錄檔和一個訊息，指出組建狀態的位置資訊。

1. 在 [偵錯]  功能表上，按一下 [啟動但不偵錯]  。

   如果您使用範例程式時，命令視窗會隨即出現，並顯示是否在集合中找到特定整數。

## <a name="next-steps"></a>後續步驟

**上一步：** [Visual C++ 中的主控台應用程式](../windows/console-applications-in-visual-cpp.md)<br/>
**下一步：** [逐步解說：在命令列編譯原生 C++ 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
