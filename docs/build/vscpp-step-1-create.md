---
title: 建立 c + + 主控台應用程式專案
description: 在 Visual c + + 中建立的 Hello World 主控台應用程式
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 3bbbd40534e3e429d68dbb6205134c57db40c851
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817721"
---
# <a name="create-a-c-console-app-project"></a>建立 c + + 主控台應用程式專案

一般起點 c + + 程式設計師為"Hello，world ！ 」 在命令列執行的應用程式。 這是什麼在您將建立 Visual Studio 在此步驟。

## <a name="prerequisites"></a>必要條件

- 具有 c + + 工作負載中，使用您的電腦上安裝和執行 Visual Studio 中使用的桌面開發。 如果它尚未安裝，請參閱[Visual Studio 2017 中的安裝 c + + 支援](vscpp-step-0-installation.md)。

## <a name="create-your-app-project"></a>建立您的應用程式專案

Visual Studio 會使用「專案」來組織應用程式的程式碼，並使用「解決方案」來組織專案。 此專案包含所有選項、 組態和用來建置您的應用程式的規則，並管理所有專案檔與任何外部檔案之間的關聯性。 若要建立您的應用程式，首先，您會建立新的專案和方案。

1. 在 Visual Studio 中開啟**檔案**功能表，然後選擇**新增 > 專案**以開啟**新專案**對話方塊。

   ![開啟 [新增專案] 對話方塊](media/vscpp-file-new-project.gif "開啟 [新增專案] 對話方塊")

1. 在 **新的專案**對話方塊中，選取**已安裝**， **Visual c + +** 如果它尚未選取，然後選擇**空專案**範本。 在 **名稱**欄位中，輸入*HelloWorld*。 選擇**確定**建立專案。

   ![命名和建立新的專案](media/vscpp-concierge-project-name-callouts.png "名稱，並建立新的專案")

Visual Studio 會建立新的空白專案，可供您針對您想要建立並加入您的原始程式碼檔的應用程式的類型特製化。 您會執行下一步。

[我遇到問題。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>主控台應用程式，使您的專案

Visual Studio 可以為 Windows 和其他平台建立各式各樣的應用程式和元件。 **空專案**尚未有關何種應用程式，它會建立特定的範本。 若要建立*主控台應用程式*，下列其中一個執行主控台或命令提示字元 視窗中，您必須告訴 Visual Studio 建置您的應用程式使用 「 主控台 」 子系統。

1. 在 Visual Studio 中開啟**專案**功能表，然後選擇**屬性**以開啟**HelloWorld 屬性頁**對話方塊。

1. 在**屬性頁** 對話方塊底下**組態屬性**，選取**連結器**，**系統**，然後選擇 編輯 方塊旁**子系統**屬性。 在 顯示下拉式功能表中，選取**主控台 (/ /SUBSYSTEM: CONSOLE)**。 選取 [確定] 儲存您的變更。

   ![開啟 [屬性頁] 對話方塊](media/vscpp-properties-linker-subsystem.gif "開啟 [屬性頁] 對話方塊")

Visual Studio 現在知道要建置您的專案，以在主控台視窗中執行。 接下來，您將加入原始程式碼檔，並輸入您的應用程式程式碼。

[我遇到問題。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>加入原始程式碼檔

1. 在 **方案總管 中**，選取 HelloWorld 專案。 在功能表列上選擇 **專案**，**加入新項目**以開啟**加入新項目**對話方塊。

1. 在 **加入新項目**對話方塊中，選取**Visual c + +** 之下**已安裝**如果已選取。 在中央窗格中，選取**c + + 檔 (.cpp)**。 變更**名稱**要*HelloWorld.cpp*。 選擇**新增**關閉對話方塊並建立該檔案。

   ![加入原始程式檔 HelloWorld.cpp](media/vscpp-add-new-item.gif "HelloWorld.cpp 加入原始程式檔")

Visual studio 會建立新的空白原始程式碼檔案，並在編輯器視窗，即可輸入您的程式碼中開啟。

[我遇到問題。](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>將程式碼加入至原始程式檔

1. 將此程式碼複製到 [HelloWorld.cpp 編輯器] 視窗中。

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   程式碼編輯器 視窗中應該看起來像這樣：

   ![Hello World 程式碼編輯器中的](media/vscpp-hello-world-editor.png "在編輯器中的 Hello World 程式碼")

在編輯器中，程式碼看起來像這樣，您就可以繼續下一個步驟，並建置您的應用程式。

[我遇到問題。](#add-a-source-code-file-issues)

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建置並執行 c + + 專案](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>疑難排解指南

來這裡解決方案常見問題的解決當您建立第一個 c + + 專案。

### <a name="create-your-app-project-issues"></a>建立您的應用程式專案的問題

如果**新的專案**不會顯示對話方塊**Visual c + +** 下的項目**已安裝**，您的 Visual Studio 複本可能沒有**桌面c + + 開發**安裝工作負載。 您可以執行安裝程式，直接從**新的專案**對話方塊。 選擇**開啟的 Visual Studio 安裝程式**再次啟動安裝程式的連結。 如果**使用者帳戶控制**對話會要求權限，選擇**是**。 在安裝程式，請確定**使用 c + + 的桌面開發**工作負載已核取，然後選擇**確定**以更新您的 Visual Studio 安裝。

如果已經存在具有相同名稱的另一個專案，選擇您的專案，另一個名稱或刪除現有的專案並再試一次。 若要刪除現有的專案，請在檔案總管中刪除方案資料夾 （包含 helloworld.sln 檔案的資料夾）。

[返回](#create-your-app-project)。

### <a name="make-your-project-a-console-app-issues"></a>主控台應用程式的問題使您的專案

如果您沒有看到**連結器**下方**組態屬性**，選擇**取消**關閉**屬性頁**對話方塊，然後請確定**HelloWorld**中選取專案**方案總管 中**，不方案或另一個檔案或資料夾，才能再試一次。

不會顯示下拉式清單控制項中，這是在**子系統**屬性編輯方塊中，直到您選取的屬性。 您可以使用指標，來選取它，或您可以按下 Tab 鍵循環的對話方塊控制項，直到**子系統**會反白顯示。 選擇下拉式清單控制項，或按 Alt + 向下鍵以開啟它。

[返回](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>新增來源的程式碼檔案的問題

如果您為來源的程式碼檔案不同的名稱，它沒有關係。 不過，請勿將新增多個原始程式碼檔，其中包含相同的程式碼到您的專案。

如果您將錯誤類型的檔案加入您的專案時，比方說，標頭檔，將它刪除並再試一次。 若要刪除檔案，請選取它在**方案總管 中**並按下 Delete 鍵。

[返回](#add-a-source-code-file)。

### <a name="add-code-to-the-source-file-issues"></a>將程式碼新增至來源檔案的問題

如果您不小心關閉來源的程式碼檔案編輯器視窗中，開啟一次，按兩下在 [HelloWorld.cpp**方案總管] 中**視窗。

如果紅色的波浪線會顯示在原始碼程式碼編輯器中的任何項目之下，請檢查您的程式碼符合拼字、 標點符號及案例的範例。 案例中佔有相當大 c + + 程式碼。

[返回](#add-code-to-the-source-file)。

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
