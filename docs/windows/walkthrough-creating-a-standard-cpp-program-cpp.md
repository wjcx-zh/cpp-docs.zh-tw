---
title: 逐步解說： 建立標準的 c + + 程式 （c + +）
ms.custom: get-started-article
ms.date: 09/18/2018
f1_keywords:
- vcfirstapp
- vccreatefirst
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 78d19a277f8bedcdbd098a662c69d6fc622a7cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647455"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>逐步解說： 建立標準的 c + + 程式 （c + +）

您可以使用 Visual Studio 整合式的開發環境 (IDE) 中的 Visual c + + 來建立標準 c + + 程式。 依照本逐步解說中的步驟，您可以建立專案、 將新檔案新增至專案、 修改檔案以加入 c + + 程式碼，然後編譯及執行使用 Visual Studio 的程式。

您可以輸入自己的 c + + 程式，或使用其中一個範例程式。 在本逐步解說的範例程式是主控台應用程式。 此應用程式使用`set`c + + 標準程式庫中的容器。

Visual c + + 會遵循 2003 c + + 標準，但有下列主要例外狀況： 兩階段名稱查閱、 例外狀況規格和匯出。 此外，Visual c + + 支援數種 c++0x 功能，比方說，lambda、 auto、 static_assert、 rvalue 參考和 extern 範本。

> [!NOTE]
> 如果需要合規性標準，使用`/Za`編譯器選項來停用標準的 Microsoft 擴充功能。 如需詳細資訊，請參閱 < [/Za，/Ze （停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md)。

## <a name="prerequisites"></a>必要條件

若要完成此逐步解說，您必須了解 C++ 語言的基礎。

### <a name="to-create-a-project-and-add-a-source-file"></a>若要建立專案並加入原始程式檔

1. 建立專案，指向**的新**上**檔案**功能表，然後按一下**專案**。

1. 在  **Visual c + +** 專案類型 窗格中，按一下  **Windows 桌面**，然後按一下**Windows 主控台應用程式**。

   > [!NOTE]
   > Visual Studio 2017，以前的版本中**新的專案**對話方塊方塊中，展開**已安裝** > **範本** >  **Visual c + +**，然後選取**Win32**。 在中央窗格中，選取 [Win32 主控台應用程式] 。

   輸入專案的名稱。

   根據預設，包含專案的方案具有相同的名稱，為專案，但您可以輸入不同的名稱。 您也可以輸入專案的不同位置。

   按一下 [確定] 建立專案。

   > [!NOTE]
   > 如需 Visual Studio 2017 以前的版本，完成**Win32 應用程式精靈**。 按一下 [**下一步**，然後確定**主控台應用程式**已選取，並取消核取**先行編譯標頭**] 方塊中。 按一下 [ **完成**]。

1. 如果**方案總管**未顯示，請在**檢視**功能表上，按一下 [**方案總管] 中**。

1. 將新的原始程式檔，如下所示新增至專案。

   1. 中**方案總管**，以滑鼠右鍵按一下**原始程式檔**資料夾，指向**新增**，然後按一下**新項目**。

   1. 在 **程式碼**節點，按一下**c + + 檔 (.cpp)**，輸入檔案的名稱，然後按一下**新增**。

   .Cpp 檔案中會出現在**原始程式檔**中的資料夾**方案總管 中**，和 Visual Studio 編輯器中開啟檔案。

1. 在檔案中在編輯器中，輸入有效的 c + + 程式，使用 c + + 標準程式庫，或複製其中一個範例程式，並將它貼在檔案中。

1. 儲存檔案。

1. 在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

   **輸出**視窗會顯示有關編譯進度，比方說，建置記錄檔和一個訊息，指出組建狀態的位置資訊。

1. 在 [偵錯] 功能表上，按一下 [啟動但不偵錯]。

   如果您使用範例程式時，命令視窗會隨即出現，並顯示是否在集合中找到特定整數。

## <a name="next-steps"></a>後續步驟

**上一步：** [主控台 Visual c + + 中的應用程式](../windows/console-applications-in-visual-cpp.md)<br/>
**下一步：** [逐步解說： 編譯命令列上的原生 c + + 程式](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>

## <a name="see-also"></a>另請參閱

[C++ 語言參考](../cpp/cpp-language-reference.md)<br/>
[C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)<br/>
