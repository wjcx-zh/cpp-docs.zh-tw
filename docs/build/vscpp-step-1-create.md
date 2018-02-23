---
title: "建立 c + + 主控台應用程式專案 |Microsoft 文件"
description: "在 Visual c + + 中建立 Hello World 主控台應用程式"
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: get-started-article
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76975054aad3173fef99a2e0f6c5ca1c642dea86
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2018
---
# <a name="create-a-c-console-app-project"></a>建立 c + + 主控台應用程式專案

一般起點 c + + 程式設計人員"Hello，world ！" 在命令列執行的應用程式。 這是功能在您將建立 Visual Studio 在此步驟。

## <a name="prerequisites"></a>必要條件

- 具有 c + + 工作負載，您的電腦上安裝並執行與桌面開發的 Visual Studio。 如果它尚未安裝，請參閱[安裝 c + + 支援 Visual Studio 中的](../build/vscpp-step-0-installation.md)。

## <a name="create-your-app-project"></a>建立應用程式專案

Visual Studio 會使用「專案」來組織應用程式的程式碼，並使用「解決方案」來組織專案。 專案包含所有選項、 組態和用來建置您的應用程式的規則，並管理專案的所有檔案和任何外部檔案之間的關聯性。 若要建立您的應用程式，首先，您會建立新的專案和方案。

1. 在 Visual Studio 中開啟**檔案**功能表，然後選擇 **新增 > 專案**開啟**新專案**對話方塊。

   ![開啟 [新增專案] 對話方塊](../build/media/vscpp-file-new-project.gif "開啟 [新增專案] 對話方塊")

1. 在**新專案**對話方塊中，選取**已安裝**， **Visual c + +**如果它尚未被選取，然後選擇 **空專案**範本。 在**名稱**欄位中，輸入*HelloWorld*。 選擇**確定**建立專案。

   ![命名和建立新的專案](../build/media/vscpp-concierge-project-name-callouts.png "名稱，並建立新的專案")

Visual Studio 建立新的空白專案，可供您針對您想要建立並加入您的原始程式碼檔的應用程式的類型特製化。 您要進行的下一步。

[我遇到問題。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>請您的專案為主控台應用程式

Visual Studio 可以建立適用於 Windows 和其他平台的所有種類的應用程式和元件。 **空專案**範本不是特定有關它所建立的應用程式種類。 若要建立*主控台應用程式*，下列其中一個執行主控台或命令提示字元 視窗中，您必須告知 Visual Studio 來建置應用程式以使用主控台子系統。

1. 在 Visual Studio 中開啟**專案**功能表，然後選擇 **屬性**開啟**HelloWorld 屬性頁**對話方塊。

1. 在**屬性頁**對話方塊底下**組態屬性**，選取**連結器**，**系統**，然後選擇 編輯方塊旁邊**子系統**屬性。 在下拉式功能表，選取**主控台 (/ 子系統： 主控台)**。 選擇**確定**以儲存變更。

   ![開啟 [屬性頁] 對話方塊](../build/media/vscpp-properties-linker-subsystem.gif "開啟屬性頁 對話方塊")

Visual Studio 現在知道建置專案，以在主控台視窗中執行。 接下來，您會加入原始程式碼檔，並輸入您的應用程式程式碼。

[我遇到問題。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>加入原始程式碼檔

1. 在**方案總管 中**，選取 HelloWorld 專案。 在功能表列上選擇 **專案**，**加入新項目**開啟**加入新項目**對話方塊。

1. 在**加入新項目**對話方塊中，選取**Visual c + +**下**已安裝**如果已選取。 在中央窗格中，選取**c + + 檔 (.cpp)**。 變更**名稱**至*HelloWorld.cpp*。 選擇**新增**關閉對話方塊並建立檔案。

   ![加入來源檔案的 HelloWorld.cpp](../build/media/vscpp-add-new-item.gif "HelloWorld.cpp 加入原始程式檔")

Visual studio 建立新的、 空的來源檔案，並開啟編輯器視窗中，輸入您的原始程式碼。

[我遇到問題。](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>將程式碼加入至原始程式檔

1. 此程式碼複製到 HelloWorld.cpp 編輯器視窗。

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   程式碼編輯器 視窗中應該看起來像這樣：

   ![Hello World 程式碼編輯器中的](../build/media/vscpp-hello-world-editor.png "編輯器中的 Hello World 程式碼")

程式碼看起來像這樣，在編輯器中，當您準備好請移至下一個步驟，並建置應用程式。

[我遇到問題。](#add-a-source-code-file-issues)

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建置並執行 c + + 專案](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>疑難排解指南

過來的解決方案常見問題的解決當您建立第一個 c + + 專案。

### <a name="create-your-app-project-issues"></a>建立您的應用程式專案的問題

如果**新專案**對話方塊不會顯示**Visual c + +**下的項目**已安裝**，您的 Visual Studio 複本可能沒有**桌面使用 c + + 開發**安裝的工作負載。 您可以執行安裝程式，直接從**新專案**對話方塊。 選擇**開啟 Visual Studio 安裝程式**再次啟動安裝程式的連結。 如果**使用者帳戶控制**，對話會要求權限，請選擇**是**。 在安裝程式，請確定**的 c + + 桌面應用程式開發**工作負載已核取，然後選擇 **確定**以更新您的 Visual Studio 安裝。

如果已經存在具有相同名稱的另一個專案，為您的專案，選擇其他名稱或刪除現有專案並再試一次。 若要刪除現有的專案，請在檔案總管中刪除方案資料夾 （包含 helloworld.sln 檔案的資料夾）。

[返回](#create-your-app-project)。

### <a name="make-your-project-a-console-app-issues"></a>主控台應用程式問題使您的專案

如果您沒有看到**連結器**底下所列**組態屬性**，選擇**取消**關閉**屬性頁**對話方塊，然後請確定**HelloWorld**中選取專案**方案總管 中**，而非從方案或另一個檔案或資料夾，然後再試一次。

不會顯示下拉式清單控制項中，這是在**子系統**屬性編輯方塊，直到您選取的屬性。 您可以使用指標，來選取它，或您可以按下 Tab 鍵循環之前的對話方塊控制項**子系統**會反白顯示。 選擇下拉式清單控制項中，或按 Alt + 向下鍵以開啟它。

[返回](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>新增來源的程式碼檔案問題

如果您提供的原始程式檔不同的名稱，它沒有關係。 不過，不要將新增多個原始程式碼檔，其中包含您的專案相同的程式碼。

如果您將錯誤類型的檔案加入您的專案，例如，標頭檔，刪除它然後再試。 若要刪除檔案，選取在**方案總管 中**並按下 Delete 鍵。

[返回](#add-a-source-code-file)。

### <a name="add-code-to-the-source-file-issues"></a>將程式碼加入來源檔案的問題

如果您不小心關閉來源的程式碼檔案編輯器視窗中，開啟一次，按兩下中 HelloWorld.cpp**方案總管 中**視窗。

如果紅色波浪線出現在原始碼程式碼編輯器中的任何資料，請檢查您的程式碼相符的拼字、 標點符號和案例的範例。 案例是重要的 c + + 程式碼中。

[返回](#add-code-to-the-source-file)。

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />