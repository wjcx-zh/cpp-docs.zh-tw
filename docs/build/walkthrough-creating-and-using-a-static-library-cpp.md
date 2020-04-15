---
title: 演練:創建和使用靜態庫 (C++)
description: 使用C++在可視化工作室中創建靜態庫 (.lib)。
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
# <a name="walkthrough-create-and-use-a-static-library"></a>演練:建立與使用靜態庫

本逐步解說示範如何建立搭配 C++ 應用程式使用的靜態程式庫 (.lib 檔案)。 使用靜態程式庫是重複使用程式碼的好方法。 而不是在每個應用中重新實現需要該功能的相同例程,而是在靜態庫中編寫一次例程,然後從應用中引用它。 從靜態庫連結的代碼將成為應用的一部分,您無需安裝另一個檔來使用該代碼。

這份逐步解說涵蓋下列工作：

- [建立靜態庫專案](#CreateLibProject)

- [新增到靜態庫](#AddClassToLib)

- [建立參考靜態庫的C++主控台應用](#CreateAppToRefTheLib)

- [使用套用式中靜態庫中的功能](#UseLibInApp)

- [執行應用程式](#RunApp)

## <a name="prerequisites"></a>Prerequisites

對 C++ 語言基本知識的了解。

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>建立靜態庫專案

有關如何創建項目的說明因可視化工作室的版本而異。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>在 Visual Studio 2019 建立靜態庫專案

1. 在功能表列上，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**程式庫**。

1. 從篩選的項目類型清單中,選擇 Windows**桌面精靈**,然後選擇 **「下一步**」 。

1. 在「**配置新項目**」頁中,在 **「專案名稱**」框中輸入*MathLibrary*以指定專案的名稱。 在 **「解決方案」 名稱**框中輸入*靜態數學*。 選擇 **「創建**」按鈕以打開**Windows 桌面項目**對話方塊。

1. 在 **「Windows 桌面項目」** 對話方塊中,在 **「應用程式類型**」下,選擇**靜態庫 (.lib)。**

1. 在 **「其他選項**」下,如果選中 **「預編譯標頭**」複選框,則取消選中該複選框。 選中「**空項目**」 的框。

1. 選擇 **「確定」** 以建立專案。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>在 Visual Studio 2017 建立靜態庫專案

1. 在選單列上,選擇 **「檔**>**新專案**>**」。。**

1. 在 **「新項目**」 對話框中,選擇 **「安裝** > **的視覺C++ Windows** > **桌面**。 在中央窗格中，選取 [Windows 傳統型精靈]****。

1. 在 **「名稱」** 框中指定項目的名稱(例如 *,MathLibrary)。* 在 **「解決方案名稱**」框中指定解決方案的名稱(例如*StaticMath)。* 選擇 [確定] **** 按鈕。

1. 在 **「Windows 桌面項目」** 對話方塊中,在 **「應用程式類型**」下,選擇**靜態庫 (.lib)。**

1. 在 **「其他選項**」下,如果選中 **「預編譯標頭**」複選框,則取消選中該複選框。 選中「**空項目**」 的框。

1. 選擇 **「確定」** 以建立專案。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>在 Visual Studio 2015 建立靜態庫專案

1. 在選單列上,選擇 **「檔**>**新專案**>**」。。**

1. 在 **「新項目**」 對話框中,選擇 **「已安裝** > **樣本** > **」可視C++** > **Win32**。 在中央窗格中，選取 [Win32 主控台應用程式] ****。

1. 在 **「名稱」** 框中指定項目的名稱(例如 *,MathLibrary)。* 在 **「解決方案名稱**」框中指定解決方案的名稱(例如*StaticMath)。* 選擇 [確定] **** 按鈕。

1. 在**Win32 應用程式精靈**中,選擇 **「下一步**」 。。

1. 在 **「應用程式設定」** 頁中,在 **「應用程式類型**」下,選擇 **「靜態庫**」。 在 **「其他選項**」下,取消選中**預編譯標頭**複選框。 選擇 **「完成」** 以建立專案。

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>新增到靜態庫

### <a name="to-add-a-class-to-the-static-library"></a>將類別加入靜態程式庫

1. 要為新類創建標題檔,請右鍵單擊以打開**解決方案資源管理器**中的**MathLibrary**專案的快捷方式功能表,然後選擇「**添加新** > **專案**」。

1. 在「**新增新項目」** 對話方塊中,選擇 **「可視C++** > **代碼**」 。。 在中間窗格中，選取 [標頭檔 (.h)] ****。 指定頭檔的名稱,例如*MathLibrary.h*,然後選擇 **「添加**」按鈕。 將顯示幾乎空白的標頭檔。

1. 添加名為的`Arithmetic`類的聲明,以執行常見數學運算,如加法、減法、乘法和除法。 代碼應類似於:

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

1. 要為新類創建源檔,請打開**解決方案資源管理器**中的**MathLibrary**專案的快捷功能表**Add** > ,然後選擇「**添加新項**」。。

1. 在「**新增新項目」** 對話框中,在中心窗格中,選擇**C++檔 (.cpp )**。 指定源檔的名稱(例如 *,MathLibrary.cpp),* 然後選擇 **「添加**」按鈕。 空白原始程式檔隨即顯示。

1. 使用此源文件實現類`Arithmetic`的功能。 代碼應類似於:

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

1. 要生成靜態庫,請在菜單欄上選擇 > **「生成生成解決方案**」 **Build** 。 生成創建一個靜態庫 *,MathLibrary.lib*,可以由其他程式使用。

   > [!NOTE]
   > 從 Visual Studio 命令列建置時，您必須以兩個步驟建置程式。 首先,運行`cl /c /EHsc MathLibrary.cpp`以編譯代碼並創建名為*MathLibrary.obj*的物件檔。(該`cl`指令呼叫編譯器 Cl.exe,`/c`該選項指定編譯而不連結。 有關詳細資訊,請參閱[/c(編譯而不連結)](../build/reference/c-compile-without-linking.md).其次,運行`lib MathLibrary.obj`以連結代碼並創建靜態庫*MathLibrary.lib*。 (`lib` 命令會叫用程式庫管理員 Lib.exe。 (如需詳細資訊，請參閱 [LIB Reference](../build/reference/lib-reference.md))。

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>建立參考靜態庫的C++主控台應用

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>建立參考 Visual Studio 2019 中的靜態庫的C++控制台應用

1. 在**解決方案資源管理器**中,右鍵單擊頂部節點 **「靜態數學」** 以打開快捷功能表。 選擇 **'新增新** > **項目**'來開啟'**新增專案**'對話框。

1. 在對話框的頂部,將**項目類型**篩選器設定為**主控台**。

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]****，然後選擇 [下一步]****。 在下一頁中,在 **「名稱」** 框中輸入*MathClient*以指定項目的名稱。

1. 選擇 [建立]**** 按鈕以建立用戶端專案。

1. 建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 這個範例中,它名為`MathClient.cpp`。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>建立參考 Visual Studio 2017 中的靜態庫的C++控制台應用

1. 在**解決方案資源管理器**中,右鍵單擊頂部節點 **「靜態數學」** 以打開快捷功能表。 選擇 **'新增新** > **項目**'來開啟'**新增專案**'對話框。

1. 在「**新增新項目**」 對話框中,選擇 **「安裝** > **的視覺C++** > **Windows 桌面**。 在中央窗格中，選取 [Windows 傳統型精靈]****。

1. 在 **「名稱」** 方塊中指定項目名稱(例如*MathClient)。* 選擇 [確定] **** 按鈕。

1. 在**Windows 桌面項目**對話方塊中,在 **「應用程式類型」** 下,選擇**主控台應用程式 (.exe)。**

1. 在 **「其他選項**」下,如果選中 **「預編譯標頭**」複選框,則取消選中該複選框。

1. 選擇 **「確定」** 以建立專案。

1. 建立主控台應用程式之後，系統會自動為您建立空白程式。 原始程式檔的名稱與您先前選擇的名稱相同。 這個範例中,它名為`MathClient.cpp`。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>建立參考 Visual Studio 2015 中的靜態庫的C++控制台應用

1. 在**解決方案資源管理器**中,右鍵單擊頂部節點 **「靜態數學」** 以打開快捷功能表。 選擇 **'新增新** > **項目**'來開啟'**新增專案**'對話框。

1. 在「**新增新項目**」 對話框中,選擇 **「已安裝** > **視覺C++** > **Win32**。 在中央窗格中，選取 [Win32 主控台應用程式] ****。

1. 在 **「名稱」** 方塊中指定項目名稱(例如*MathClient)。* 選擇 [確定] **** 按鈕。

1. 在**Win32 應用程式精靈**對話框中,選擇 **「下一步**」 。。

1. 在 **「應用程式設定」** 頁上,在 **「應用程式類型**」 下,請確保選擇了**主控台應用程式**。 在 **「其他選項**」下,取消選中**預編譯標頭**,然後選中 **「空項目**」複選框。 選擇 **「完成」** 以建立專案。

1. 要將源檔案添加到空專案中,請右鍵單擊以打開**解決方案資源管理器**中的**MathClient**專案的快捷方式選單,然後選擇「**添加新**>**項**」。

1. 在「**新增新項目」** 對話方塊中,選擇 **「可視C++** > **代碼**」 。。 在中間窗格中，選取 [C++ 檔 (.cpp)] ****。 指定來源檔案名稱(例如*MathClient.cpp),* 然後選擇 **「添加**」按鈕。 空白原始程式檔隨即顯示。

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>使用套用式中靜態庫中的功能

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>在應用程式中使用靜態程式庫的功能

1. 您必須先參考數學常式，才能在靜態程式庫中使用它。 在**解決方案資源管理器**中打開**MathClient**專案的快捷功能表,然後選擇 **「添加** > **參考**」。。

1. [加入參考] **** 對話方塊會列出您可以參考的程式庫。 項目 **「** 選項卡列出目前解決方案中的專案及其引用的任何庫。 開啟「**項目**」 選項卡,選擇 **「數學庫**」複選框,然後選擇「**確定**」 按鈕。

1. 要引用`MathLibrary.h`標頭檔,必須修改包含的目錄路徑。 在**解決方案資源管理器**中,右鍵單擊**MathClient**以打開快捷功能表。 選擇 **「屬性**」 以開啟 **「數學用戶端屬性頁」** 對話方塊。

1. 在 **"MathClient 屬性頁**"對話框中,將 **「設定**」下拉至 **「所有設定**」。 將**平臺**下拉清單設置為 **「所有平臺**」。

1. 選擇**配置屬性** > **C/C++** > **一般**屬性頁。 在 **"其他包含目錄"** 屬性中,指定**MathLibrary**目錄的路徑,或流覽該目錄。

   要瀏覽目錄路徑:

   1. 開啟 **「其他包含目錄**」屬性值下拉清單,然後選擇 **「編輯**」。

   1. 在「**其他包含目錄」** 對話框中,按兩下文字框頂部。 然後選擇行尾的省略號按鈕 (**...)。**

   1. 在 **「選擇目錄」** 對話方塊中,向上導航一個級別,然後選擇**MathLibrary**目錄。 然後選擇 **「選擇資料夾」** 按鈕以儲存您的選擇。

   1. 在「**其他包含目錄」對話框中**,選擇「**確定」** 按鈕。

   1. 在「**屬性頁」** 對話框中,選擇「**確定**」按鈕以儲存對專案的更改。

1. 現在,`Arithmetic`您可以通過在代碼中包含標頭來使用此`#include "MathLibrary.h"`應用中的 類別。 將`MathClient.cpp`的內容 取代為以下代碼:

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

1. 要產生執行檔,請選擇**Build** > 選單列上的**產生產生解決方案**。

## <a name="run-the-app"></a><a name="RunApp"></a>執行應用

### <a name="to-run-the-app"></a>執行應用程式

1. 確保**MathClient**被選為預設專案。 要選擇它,請右鍵單擊以打開**解決方案資源管理器**中的**MathClient**的快捷功能表,然後選擇「**設定為啟動專案**」 。

1. 要運行專案,在功能表欄上,選擇 **「不調試即可啟動調試** **Debug**  >  」。 輸出應類似於:

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>另請參閱

[演練:建立和使用動態連結庫 (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[傳統型應用程式 (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
