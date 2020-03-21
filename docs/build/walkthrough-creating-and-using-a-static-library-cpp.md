---
title: 逐步解說：建立和使用靜態程式庫 (C++)
description: 使用C++在 Visual Studio 中建立靜態程式庫（.lib）。
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: c81ccd970383c8571a7d0d1e77d4b8fe44900bcf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078185"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>逐步解說：建立和使用靜態程式庫 (C++)

本逐步解說示範如何建立搭配 C++ 應用程式使用的靜態程式庫 (.lib 檔案)。 使用靜態程式庫是重複使用程式碼的好方法。 不是在每個需要功能的應用程式中重新實作不免相同的常式，而是在靜態程式庫中撰寫一次，然後從應用程式參考它。 從靜態程式庫連結的程式碼會變成應用程式的一部分，您不必安裝另一個檔案即可使用程式碼。

這份逐步解說涵蓋下列工作：

- [建立靜態程式庫專案](#CreateLibProject)

- [將類別加入靜態程式庫](#AddClassToLib)

- [建立參考靜態程式庫的 C++ 主控台應用程式](#CreateAppToRefTheLib)

- [在應用程式中使用靜態程式庫的功能](#UseLibInApp)

- [執行應用程式](#RunApp)

## <a name="prerequisites"></a>Prerequisites

對 C++ 語言基本知識的了解。

##  <a name="creating-a-static-library-project"></a><a name="CreateLibProject"></a> 建立靜態程式庫專案

如何建立專案的指示會根據您使用的是 Visual Studio 2019 還是舊版而有所不同。 請確定您已在此頁面的左上方設定正確的版本。

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立靜態程式庫專案

1. 在功能表列上 **，選擇 [** 檔案] > [**新增**>**專案**]，開啟 [**建立新的專案**] 對話方塊。

1. 在對話方塊頂端，將 [語言] 設定為 **C++** ，將 [平台] 設定為 **Windows**，並將 [專案類型] 設定為**程式庫**。

1. 從篩選過的專案類型清單中，選擇 [**靜態程式庫**]，然後選擇 **[下一步]** 。 在下一個頁面的 [**名稱**] 方塊中，輸入*MathFuncsLib*以指定專案的名稱，並視需要指定專案位置。

1. 選擇 [建立] 按鈕以建立用戶端專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>若要在 Visual Studio 2017 中建立靜態程式庫專案

1. 在功能表列上 **，選擇 [** 檔案] > [**新增**>**專案**]。

1. 在 [**新增專案**] 對話方塊的左窗格中，展開 [**已安裝**的 >  **C++視覺效果**]，然後選取 [ **Windows 桌面**]。 在中央窗格中，選取 [Windows 傳統型精靈]。

1. 在 [名稱]方塊中指定專案的名稱，例如 **MathFuncsLib** 。 在 [方案名稱]方塊中指定方案的名稱，例如 **StaticLibrary** 。 選擇 [確定] 按鈕。

1. 在 [**應用程式類型**] 底下，選取 **[靜態程式庫（.lib）** ]。

1. 在 [**其他選項**] 底下，取消選取 [先行**編譯頭**檔] 核取方塊。

1. 選擇 [**確定]** 以建立專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中建立靜態程式庫專案

1. 在功能表列上 **，選擇 [** 檔案] > [**新增**>**專案**]。

1. 在 **新增專案** 對話方塊中，展開 **已安裝**的 > **範本** > **視覺C++效果**，然後選取  **Win32**。 在中央窗格中，選取 [Win32 主控台應用程式]。

1. 在 [名稱]方塊中指定專案的名稱，例如 **MathFuncsLib** 。 在 [方案名稱]方塊中指定方案的名稱，例如 **StaticLibrary** 。 選擇 [確定] 按鈕。

1. 按 [下一步]。

1. 在 [**應用程式類型**] 底下，選取 [**靜態程式庫**]。 然後取消核取 [先行**編譯標題**] 方塊，然後選擇 **[完成]** 。

::: moniker-end

##  <a name="adding-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> 將類別加入靜態程式庫

### <a name="to-add-a-class-to-the-static-library"></a>將類別加入靜態程式庫

1. 若要建立新類別的標頭檔，請在**方案總管**中開啟**MathFuncsLib**專案的快捷方式功能表，然後選擇 [**加入** > **新專案**]。 在 [加入新項目] 對話方塊的左窗格中，選取 [Visual C++]底下的 [程式碼]。 在中間窗格中，選取 [標頭檔 (.h)]。 指定標頭檔的名稱 (例如 *MathFuncsLib.h*)，然後選擇 [加入] 按鈕。 空白標頭檔隨即顯示。

1. 新增名為 `MyMathFuncs` 的類別，以執行一般的數學運算，例如加法、減法、乘法和除法。 程式碼應該類似：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. 若要建立新類別的原始程式檔，請在**方案總管**中開啟**MathFuncsLib**專案的快捷方式功能表，然後選擇 [**加入** > **新專案**]。 在 [加入新項目] 對話方塊的左窗格中，選取 [Visual C++]底下的 [程式碼]。 在中間窗格中，選取 [C++ 檔 (.cpp)]。 指定原始程式檔的名稱 (例如 *MathFuncsLib.cpp*)，然後選擇 [加入] 按鈕。 空白原始程式檔隨即顯示。

1. 使用這個原始程式檔來實作 **MyMathFuncs**的功能。 程式碼應該類似：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. 選取功能表列上的 [**建立** > **組建方案**]，以編譯靜態程式庫。 編譯會建立可供其他程式使用的靜態程式庫。

   > [!NOTE]
   > 從 Visual Studio 命令列建置時，您必須以兩個步驟建置程式。 首先，執行 `cl /c /EHsc MathFuncsLib.cpp` 來編譯器代碼，並建立名為 `MathFuncsLib.obj`的物件檔案。 (`cl` 命令會叫用編譯器 Cl.exe，而 `/c` 選項則指定編譯但不連結。 如需詳細資訊，請參閱[/c （編譯而不連結）](../build/reference/c-compile-without-linking.md)。第二，執行 `lib MathFuncsLib.obj` 以連結程式代碼，並建立靜態程式庫 `MathFuncsLib.lib`。 (`lib` 命令會叫用程式庫管理員 Lib.exe。 (如需詳細資訊，請參閱 [LIB Reference](../build/reference/lib-reference.md))。

##  <a name="creating-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> 建立參考靜態程式庫的 C++ 主控台應用程式

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>若要建立C++在 Visual Studio 2019 中參考靜態程式庫的主控台應用程式

1. 在**方案總管**中，以滑鼠右鍵按一下方案的最上層節點，然後選擇 [**加入**>**新增專案**] 以開啟 [新增**專案**] 對話方塊。

1. 在對話方塊頂端，將 [語言] 設定為 **C++** ，將 [平台] 設定為 **Windows**，並將 [專案類型] 設定為**主控台**。

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]，然後選擇 [下一步]。 在下一個頁面的 [**名稱**] 方塊中，輸入*MyExecRefsLib*以指定專案的名稱，並視需要指定專案位置。

1. 選擇 [建立] 按鈕以建立用戶端專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>若要建立C++在 Visual Studio 2017 中參考靜態程式庫的主控台應用程式

1. 在功能表列上 **，選擇 [** 檔案] > [**新增**>**專案**]。

1. 在 [**新增專案**] 對話方塊的左窗格中，展開 [**已安裝**的 >  **C++視覺效果**]，然後選取 [ **Windows 桌面**]。 在中央窗格中，選取 [Windows 傳統型精靈]。

1. 在 [名稱]方塊中指定專案的名稱，例如 **MyExecRefsLib** 。 在 [方案]旁邊的下拉式清單中，選取 [加入至方案]。 命令會將新專案新增至包含靜態程式庫的方案。 選擇 [確定] 按鈕。

1. 在 [**應用程式類型**] 底下，選取 **[主控台應用程式（.exe）** ]。

1. 在 [**其他選項**] 底下，取消選取 [先行**編譯頭**檔] 核取方塊。

1. 選擇 [**確定]** 以建立專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>若要建立C++在 Visual Studio 2015 中參考靜態程式庫的主控台應用程式

1. 在功能表列上 **，選擇 [** 檔案] > [**新增**>**專案**]。

1. 在 **新增專案** 對話方塊中，展開 **已安裝**的 > **範本** > **視覺C++效果**，然後選取  **Win32**。 在中央窗格中，選取 [Win32 主控台應用程式]。

1. 在 [名稱]方塊中指定專案的名稱，例如 **MyExecRefsLib** 。 在 [方案]旁邊的下拉式清單中，選取 [加入至方案]。 命令會將新專案新增至包含靜態程式庫的方案。 選擇 [確定] 按鈕。

1. 按 [下一步]。

1. 請確定已選取 [**主控台應用程式**]。 然後，核取 [**空的專案**] 方塊，然後選擇 **[完成]** 。

::: moniker-end

##  <a name="using-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> 在應用程式中使用靜態程式庫的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在應用程式中使用靜態程式庫的功能

1. 建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 在此範例中，它的名稱為 `MyExecRefsLib.cpp`。

1. 您必須先參考數學常式，才能在靜態程式庫中使用它。 在**方案總管**中，開啟**MyExecRefsLib**專案的快捷方式功能表，然後選擇 [**加入** > **參考**]。

1. [加入參考] 對話方塊會列出您可以參考的程式庫。 [**專案**] 索引標籤會列出目前方案中的專案，以及它們所參考的任何程式庫。 在 [專案] 索引標籤上，選取 [MathFuncsLib] 核取方塊，然後選擇 [確定] 按鈕。

1. 若要參考 `MathFuncsLib.h` 標頭檔，您必須修改內含的目錄路徑。 在 **MyExecRefsLib** 的 [屬性頁]對話方塊中，依序展開 [組態屬性] 節點、[C/C++] 節點，然後選取 [一般]。 在 [**其他 Include 目錄**] 旁邊，指定**MathFuncsLib**目錄的路徑，或流覽它。

   若要瀏覽至目錄路徑，請開啟屬性值下拉式清單，然後選擇 [編輯]。 在 [**其他 Include 目錄**] 對話方塊的文字方塊中，選取空白行，然後選擇行尾的省略號按鈕（ **...** ）。 在 [選取目錄] 對話方塊中，選取 **MathFuncsLib** 目錄，然後選擇 [選取資料夾] 按鈕以儲存選取項目並關閉對話方塊。 在 [其他 Include 目錄] 對話方塊中，選擇 [確定] 按鈕，然後在 [屬性頁] 對話方塊中選擇 [確定] 按鈕，將您的變更儲存至專案。

1. 您現在可以在程式碼中包含 `#include "MathFuncsLib.h"` 標頭，以在此應用程式中使用 `MyMathFuncs` 類別。 將 `MyExecRefsLib.cpp` 的內容取代為下列程式碼：

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. 選擇功能表列上的 [**組建** > **組建方案**] 來建立可執行檔。

##  <a name="running-the-app"></a><a name="RunApp"></a> 執行應用程式

### <a name="to-run-the-app"></a>執行應用程式

1. 在方案總管 中開啟 **MyExecRefsLib** 的捷徑功能表，然後選擇 [設定為啟始專案]，確定已選取 **MyExecRefsLib**做為預設專案。

1. 若要執行專案，請在功能表列上選擇 [偵錯] > [啟動但不偵錯]。 輸出應該類似：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>另請參閱

[逐步解說：建立和使用動態連結程式庫 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[傳統型應用程式 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
