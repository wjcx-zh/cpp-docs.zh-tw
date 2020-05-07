---
title: 逐步解說：建立和使用靜態程式庫（c + +）
description: 使用 c + + 在 Visual Studio 中建立靜態程式庫（.lib）。
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335142"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>逐步解說：建立和使用靜態程式庫

本逐步解說示範如何建立搭配 C++ 應用程式使用的靜態程式庫 (.lib 檔案)。 使用靜態程式庫是重複使用程式碼的好方法。 不是在每個需要功能的應用程式中重新實作不免相同的常式，而是在靜態程式庫中撰寫一次，然後從應用程式參考它。 從靜態程式庫連結的程式碼會成為應用程式的一部分，您不需要安裝另一個檔案就能使用該程式碼。

這份逐步解說涵蓋下列工作：

- [建立靜態程式庫專案](#CreateLibProject)

- [將類別新增至靜態程式庫](#AddClassToLib)

- [建立參考靜態程式庫的 c + + 主控台應用程式](#CreateAppToRefTheLib)

- [在應用程式中使用靜態程式庫的功能](#UseLibInApp)

- [執行應用程式](#RunApp)

## <a name="prerequisites"></a>必要條件

對 C++ 語言基本知識的了解。

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>建立靜態程式庫專案

根據您的 Visual Studio 版本而定，如何建立專案的指示會有所不同。 若要查看您慣用版本 Visual Studio 的檔，請使用**版本**選取器控制項。 您可在此頁面的目錄頂端找到該檔案。

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立靜態程式庫專案

1. 在功能表列上，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**程式庫**。

1. 從篩選過的專案類型清單中，選取 [ **Windows 桌面] [Wizard]**，然後選擇 **[下一步**]。

1. 在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入*MathLibrary* ，以指定專案的名稱。 在 [**方案名稱**] 方塊中，輸入*StaticMath* 。 選擇 [**建立**] 按鈕以開啟 [ **Windows 桌面專案**] 對話方塊。

1. 在 [ **Windows 桌面專案**] 對話方塊的 [**應用程式類型**] 底下，選取 **[靜態程式庫（.lib）**]。

1. 在 [**其他選項**] 底下，取消核取 [先行**編譯頭**檔] 核取方塊（如果已勾選） 勾選 [**空的專案**] 方塊。

1. 選擇 [**確定]** 以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>若要在 Visual Studio 2017 中建立靜態程式庫專案

1. 在功能表列上 **，選擇 [** >檔案] [**新增** > ] [**專案**]。

1. 在 [**新增專案**] 對話方塊中，選取 [**已安裝** > **Visual C++** > **Windows 桌面**]。 在中央窗格中，選取 [Windows 傳統型精靈]****。

1. 在 [**名稱**] 方塊中指定專案的名稱（例如， *MathLibrary*）。 在 [**方案名稱**] 方塊中指定解決方案的名稱（例如， *StaticMath*）。 選擇 [確定] **** 按鈕。

1. 在 [ **Windows 桌面專案**] 對話方塊的 [**應用程式類型**] 底下，選取 **[靜態程式庫（.lib）**]。

1. 在 [**其他選項**] 底下，取消核取 [先行**編譯頭**檔] 核取方塊（如果已勾選） 勾選 [**空的專案**] 方塊。

1. 選擇 [**確定]** 以建立專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中建立靜態程式庫專案

1. 在功能表列上 **，選擇 [** >檔案] [**新增** > ] [**專案**]。

1. 在 [**新增專案**] 對話方塊中，選取 [**已安裝** > **範本** > **Visual C++** > **Win32**]。 在中央窗格中，選取 [Win32 主控台應用程式] ****。

1. 在 [**名稱**] 方塊中指定專案的名稱（例如， *MathLibrary*）。 在 [**方案名稱**] 方塊中指定解決方案的名稱（例如， *StaticMath*）。 選擇 [確定] **** 按鈕。

1. 在**Win32 應用程式精靈**中，選擇 **[下一步]**。

1. 在 [**應用程式設定**] 頁面的 [**應用程式類型**] 底下，選取 [**靜態程式庫**]。 在 [**其他選項**] 下方，取消選取 [先行**編譯頭**檔] 核取方塊 選擇 **[完成]** 以建立專案。

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>將類別新增至靜態程式庫

### <a name="to-add-a-class-to-the-static-library"></a>將類別加入靜態程式庫

1. 若要建立新類別的標頭檔，請以滑鼠右鍵按一下以在**方案總管**中開啟**MathLibrary**專案的快捷方式功能表，然後選擇 [**加入** > **新專案**]。

1. 在 [**加入新專案**] 對話方塊中，選取 [ **Visual C++** > 程式**代碼**]。 在中間窗格中，選取 [標頭檔 (.h)] ****。 指定標頭檔的名稱（例如*MathLibrary*），然後選擇 [**新增**] 按鈕。 會顯示近乎空白的標頭檔。

1. 新增名`Arithmetic`為的類別宣告，以執行一般的數學運算，例如加法、減法、乘法和除法。 程式碼應該類似：

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. 若要建立新類別的原始程式檔，請在**方案總管**中開啟**MathLibrary**專案的快捷方式功能表，然後選擇 [**加入** > **新專案**]。

1. 在 [**加入新專案**] 對話方塊的中央窗格中，選取 [ **c + + 檔案（.cpp）**]。 指定原始程式檔的名稱（例如*MathLibrary*），然後選擇 [**新增**] 按鈕。 空白原始程式檔隨即顯示。

1. 使用此原始程式檔來執行類別`Arithmetic`的功能。 程式碼應該類似：

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. 若要建立靜態程式庫，請在功能表列上選取 [**組建** > ] [組建**方案**]。 組建會建立可供其他程式使用的靜態程式庫（ *MathLibrary*）。

   > [!NOTE]
   > 從 Visual Studio 命令列建置時，您必須以兩個步驟建置程式。 首先，執行`cl /c /EHsc MathLibrary.cpp`來編譯器代碼並建立名為*MathLibrary*的物件檔案。（此`cl`命令會叫用編譯器、Cl .exe，而選項`/c`則指定編譯而不連結。 如需詳細資訊，請參閱[/c （編譯而不連結）](../build/reference/c-compile-without-linking.md)。第二， `lib MathLibrary.obj`執行以連結程式代碼，並建立靜態程式庫*MathLibrary*。 (`lib` 命令會叫用程式庫管理員 Lib.exe。 (如需詳細資訊，請參閱 [LIB Reference](../build/reference/lib-reference.md))。

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>建立參考靜態程式庫的 c + + 主控台應用程式

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立參考靜態程式庫的 c + + 主控台應用程式

1. 在**方案總管**中，以滑鼠右鍵按一下最上層節點 [**方案 ' StaticMath '**] 以開啟快捷方式功能表。 選擇 [**加入** > **新專案**] 以開啟 [新增**專案**] 對話方塊。

1. 在對話方塊頂端，將 [**專案類型**] 篩選器設定為 [**主控台**]。

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]****，然後選擇 [下一步]****。 在下一個頁面的 [**名稱**] 方塊中輸入*MathClient* ，以指定專案的名稱。

1. 選擇 [建立]**** 按鈕以建立用戶端專案。

1. 建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 在範例中，它的名稱`MathClient.cpp`為。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>若要在 Visual Studio 2017 中建立參考靜態程式庫的 c + + 主控台應用程式

1. 在**方案總管**中，以滑鼠右鍵按一下最上層節點 [**方案 ' StaticMath '**] 以開啟快捷方式功能表。 選擇 [**加入** > **新專案**] 以開啟 [新增**專案**] 對話方塊。

1. 在 [**加入新的專案**] 對話方塊中，選取 [**已安裝** > **Visual C++** > **Windows 桌面**]。 在中央窗格中，選取 [Windows 傳統型精靈]****。

1. 在 [**名稱**] 方塊中指定專案的名稱（例如， *MathClient*）。 選擇 [確定] **** 按鈕。

1. 在 [ **Windows 桌面專案**] 對話方塊的 [**應用程式類型**] 底下，選取 **[主控台應用程式（.exe）**]。

1. 在 [**其他選項**] 底下，取消核取 [先行**編譯頭**檔] 核取方塊（如果已勾選）

1. 選擇 [**確定]** 以建立專案。

1. 建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 在範例中，它的名稱`MathClient.cpp`為。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>若要在 Visual Studio 2015 中建立參考靜態程式庫的 c + + 主控台應用程式

1. 在**方案總管**中，以滑鼠右鍵按一下最上層節點 [**方案 ' StaticMath '**] 以開啟快捷方式功能表。 選擇 [**加入** > **新專案**] 以開啟 [新增**專案**] 對話方塊。

1. 在 [**加入新的專案**] 對話方塊中，選取 [**已安裝** > **Visual C++** > **Win32**]。 在中央窗格中，選取 [Win32 主控台應用程式] ****。

1. 在 [**名稱**] 方塊中指定專案的名稱（例如， *MathClient*）。 選擇 [確定] **** 按鈕。

1. 在 [ **Win32 應用程式精靈**] 對話方塊中，選擇 [**下一步**]。

1. 在 [**應用程式設定**] 頁面的 [**應用程式類型**] 底下，確認已選取 [**主控台應用程式**]。 在 [**其他選項**] 底下，取消核取 [先行**編譯頭**檔]，然後核取 [**空專案** 選擇 **[完成]** 以建立專案。

1. 若要將原始程式檔加入至空的專案，請以滑鼠右鍵按一下以在**方案總管**中開啟**MathClient**專案的快捷方式功能表，然後選擇 [**加入** > **新專案**]。

1. 在 [**加入新專案**] 對話方塊中，選取 [ **Visual C++** > 程式**代碼**]。 在中間窗格中，選取 [C++ 檔 (.cpp)] ****。 指定原始程式檔的名稱（例如*MathClient*），然後選擇 [**新增**] 按鈕。 空白原始程式檔隨即顯示。

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>在應用程式中使用靜態程式庫的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在應用程式中使用靜態程式庫的功能

1. 您必須先參考數學常式，才能在靜態程式庫中使用它。 在**方案總管**中，開啟**MathClient**專案的快捷方式功能表，然後選擇 [**加入** > **參考**]。

1. [加入參考] **** 對話方塊會列出您可以參考的程式庫。 [**專案**] 索引標籤會列出目前方案中的專案，以及它們所參考的任何程式庫。 開啟 [**專案**] 索引標籤，選取 [ **MathLibrary** ] 核取方塊，然後選擇 [**確定]** 按鈕。

1. 若要參考`MathLibrary.h`標頭檔，您必須修改內含的目錄路徑。 在**方案總管**中，以滑鼠右鍵按一下 [ **MathClient** ] 以開啟快捷方式功能表。 選擇 [**屬性**] 以開啟 [ **MathClient 屬性頁**] 對話方塊。

1. 在 [ **MathClient 屬性頁**] 對話方塊中，將 **[設定**] 下拉式方塊設為 [**所有**設定]。 將 [**平臺**] 下拉式選設定為 [**所有平臺**]。

1. 選取 [設定**屬性** > ] [**c/c + +** > **一般**] 屬性頁。 在 [**其他 Include 目錄**] 屬性中，指定**MathLibrary**目錄的路徑，或流覽它。

   流覽目錄路徑：

   1. 開啟 [**其他 Include 目錄**] 屬性值下拉式清單，然後選擇 [**編輯**]。

   1. 在 [**其他 Include 目錄**] 對話方塊中，按兩下文字方塊的頂端。 然後選擇行尾的省略號按鈕（**...**）。

   1. 在 [**選取目錄**] 對話方塊中，流覽 [層級]，然後選取 [ **MathLibrary** ] 目錄。 然後選擇 [**選取資料夾**] 按鈕以儲存您的選取專案。

   1. 在 [**其他 Include 目錄**] 對話方塊中，選擇 [**確定]** 按鈕。

   1. 在 [**屬性頁**] 對話方塊中，選擇 [**確定]** 按鈕，將您的變更儲存至專案。

1. 您現在可以在程式`Arithmetic`代碼中包含`#include "MathLibrary.h"`標頭，以在此應用程式中使用類別。 將的內容取代`MathClient.cpp`為下列程式碼：

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. 若要建立可執行檔，請在功能表列上選擇 [**組建** > ] [組建**方案**]。

## <a name="run-the-app"></a><a name="RunApp"></a>執行應用程式

### <a name="to-run-the-app"></a>執行應用程式

1. 請確定已選取 [ **MathClient** ] 做為預設專案。 若要選取此專案，請以滑鼠右鍵按一下以在**方案總管**中開啟**MathClient**的快捷方式功能表，然後選擇 [**設定為啟始專案**]。

1. 若要執行專案，請在功能表列上選擇 [不進行調試的**Debug** > **啟動**]。 輸出應該類似：

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>請參閱

[逐步解說：建立和使用動態連結程式庫（c + +）](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[傳統型應用程式 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
