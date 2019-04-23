---
title: 逐步解說：建立和使用靜態程式庫 (C++)
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: 0d527681abb077a01b3d902c092a21de7a052867
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59031504"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>逐步解說：建立和使用靜態程式庫 (C++)

本逐步解說示範如何建立搭配 C++ 應用程式使用的靜態程式庫 (.lib 檔案)。 使用靜態程式庫是重複使用程式碼的好方法。 而不是重新實作相同的常式，在需要的功能，您將它們寫入其中的每個應用程式時間的靜態程式庫，然後參考它從應用程式。 從靜態程式庫連結的程式碼會變成應用程式的一部分，您不必安裝另一個檔案即可使用程式碼。

這份逐步解說涵蓋下列工作：

- [建立靜態程式庫專案](#CreateLibProject)

- [將類別加入靜態程式庫](#AddClassToLib)

- [建立參考靜態程式庫的 C++ 主控台應用程式](#CreateAppToRefTheLib)

- [在應用程式中使用靜態程式庫的功能](#UseLibInApp)

- [執行應用程式](#RunApp)

## <a name="prerequisites"></a>必要條件

對 C++ 語言基本知識的了解。

##  <a name="CreateLibProject"></a> 建立靜態程式庫專案

### <a name="to-create-a-static-library-project"></a>建立靜態程式庫專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

1. 在左窗格中**新的專案**對話方塊方塊中，展開**已安裝** > **Visual C++** ，然後選取  **Windows Desktop**. 在中央窗格中，選取**Windows Desktop 精靈**。

   > [!NOTE]
   > Visual Studio 2017，以前的版本中**新的專案**對話方塊方塊中，展開**已安裝** > **範本** >  **視覺化C++** ，然後選取**Win32**。 在中央窗格中，選取 [Win32 主控台應用程式] 。

1. 在 [名稱] 方塊中指定專案的名稱，例如 **MathFuncsLib** 。 在 [方案名稱] 方塊中指定方案的名稱，例如 **StaticLibrary** 。 選擇 [確定]  按鈕。

    - Visual Studio 2017，

        1. 底下**應用程式類型**，選取**靜態程式庫 (.lib)**。

        1. 底下**其他選項**，取消核取**先行編譯標頭**核取方塊。

        1. 選擇**確定**建立專案。

    - Visual Studio 2017，以前的版本

        1. 按 [ **下一步**]。

        1. 底下**應用程式類型**，選取**靜態程式庫**。 然後取消核取**先行編譯標頭**方塊，然後選擇**完成**。

##  <a name="AddClassToLib"></a> 將類別加入靜態程式庫

### <a name="to-add-a-class-to-the-static-library"></a>將類別加入靜態程式庫

1. 若要建立新的類別的標頭檔，開啟捷徑功能表**MathFuncsLib**專案中**方案總管**，然後選擇**新增** >  **新的項目**。 在 [加入新項目]  對話方塊的左窗格中，選取 [Visual C++] 底下的 [程式碼] 。 在中間窗格中，選取 [標頭檔 (.h)] 。 指定標頭檔的名稱 (例如 *MathFuncsLib.h*)，然後選擇 [加入]  按鈕。 空白標頭檔隨即顯示。

1. 新增類別，名為`MyMathFuncs`來執行一般算術運算，例如加法、 減法、 乘法和除法。 程式碼應該類似：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. 若要建立新的類別的原始程式檔，開啟捷徑功能表**MathFuncsLib**專案中**方案總管**，然後選擇**新增** >  **新的項目**。 在 [加入新項目]  對話方塊的左窗格中，選取 [Visual C++] 底下的 [程式碼] 。 在中間窗格中，選取 [C++ 檔 (.cpp)] 。 指定原始程式檔的名稱 (例如 *MathFuncsLib.cpp*)，然後選擇 [加入]  按鈕。 空白原始程式檔隨即顯示。

1. 使用這個原始程式檔來實作 **MyMathFuncs**的功能。 程式碼應該類似：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. 選取編譯靜態程式庫**建置** > **建置方案**功能表列上。 編譯時，會建立可供其他程式的靜態程式庫。

   > [!NOTE]
   > 從 Visual Studio 命令列建置時，您必須以兩個步驟建置程式。 首先，執行`cl /c /EHsc MathFuncsLib.cpp`編譯的程式碼，並建立物件的檔案，稱為`MathFuncsLib.obj`。 (`cl` 命令會叫用編譯器 Cl.exe，而 `/c` 選項則指定編譯但不連結。 如需詳細資訊，請參閱 < [/c （編譯而不連結）](../build/reference/c-compile-without-linking.md)。)其次，執行`lib MathFuncsLib.obj`以連結程式碼並建立靜態程式庫`MathFuncsLib.lib`。 (`lib` 命令會叫用程式庫管理員 Lib.exe。 (如需詳細資訊，請參閱 [LIB Reference](../build/reference/lib-reference.md))。

##  <a name="CreateAppToRefTheLib"></a> 建立參考靜態程式庫的 C++ 主控台應用程式

### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>建立參考靜態程式庫的 C++ 主控台應用程式

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

1. 在左窗格中**新的專案**對話方塊方塊中，展開**已安裝** > **Visual C++** ，然後選取  **Windows Desktop**. 在中央窗格中，選取**Windows Desktop 精靈**。

   > [!NOTE]
   > Visual Studio 2017，以前的版本中**新的專案**對話方塊方塊中，展開**已安裝** > **範本** >  **視覺化C++** ，然後選取**Win32**。 在中央窗格中，選取 [Win32 主控台應用程式] 。

1. 在 [名稱] 方塊中指定專案的名稱，例如 **MyExecRefsLib** 。 在 [方案] 旁邊的下拉式清單中，選取 [加入至方案] 。 此命令會將新的專案加入至包含靜態程式庫的方案。 選擇 [確定]  按鈕。

    - Visual Studio 2017，

        1. 底下**應用程式類型**，選取**主控台應用程式 (.exe)**。

        1. 底下**其他選項**，取消核取**先行編譯標頭**核取方塊。

        1. 選擇**確定**建立專案。

    - Visual Studio 2017，以前的版本

        1. 按 [ **下一步**]。

        1. 請確定**主控台應用程式**已選取。 然後檢查**空專案**方塊，然後選擇**完成**。

##  <a name="UseLibInApp"></a> 在應用程式中使用靜態程式庫的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在應用程式中使用靜態程式庫的功能

1. 建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 在範例中，它會命名為`MyExecRefsLib.cpp`。

1. 您必須先參考數學常式，才能在靜態程式庫中使用它。 開啟捷徑功能表**MyExecRefsLib**專案中**方案總管**，然後選擇**新增** > **參考**.

1. [加入參考]  對話方塊會列出您可以參考的程式庫。 **專案** 索引標籤會列出目前的方案和它們所參考的任何程式庫中的專案。 在 [專案]  索引標籤上，選取 [MathFuncsLib]  核取方塊，然後選擇 [確定]  按鈕。

1. 參考`MathFuncsLib.h`標頭檔，您必須修改包含的目錄路徑。 在 **MyExecRefsLib** 的 [屬性頁] 對話方塊中，依序展開 [組態屬性]  節點、[C/C++]  節點，然後選取 [一般] 。 旁**其他 Include 目錄**，指定的路徑**MathFuncsLib**目錄或瀏覽至它。

   若要瀏覽至目錄路徑，請開啟屬性值下拉式清單，然後選擇 [編輯] 。 在 **其他 Include 目錄**對話方塊中，在文字方塊中，選取空白行，然後選擇 省略符號按鈕 (**...**) 結尾的行。 在 [選取目錄]  對話方塊中，選取 **MathFuncsLib** 目錄，然後選擇 [選取資料夾]  按鈕以儲存選取項目並關閉對話方塊。 在 [其他 Include 目錄]  對話方塊中，選擇 [確定]  按鈕，然後在 [屬性頁]  對話方塊中選擇 [確定]  按鈕，將您的變更儲存至專案。

1. 您現在可以使用`MyMathFuncs`包含此應用程式中的類別`#include "MathFuncsLib.h"`程式碼中的標頭。 內容取代`MyExecRefsLib.cpp`以下列程式碼：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. 選擇來建立可執行檔**建置** > **建置方案**功能表列上。

##  <a name="RunApp"></a> 執行應用程式

### <a name="to-run-the-app"></a>執行應用程式

1. 在方案總管  中開啟 **MyExecRefsLib** 的捷徑功能表，然後選擇 [設定為啟始專案] ，確定已選取 **MyExecRefsLib**做為預設專案。

1. 若要執行專案，請在功能表列上選擇 [偵錯] > [啟動但不偵錯]。 輸出應類似於：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>另請參閱

[逐步解說：建立和使用動態連結程式庫 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[傳統型應用程式 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
