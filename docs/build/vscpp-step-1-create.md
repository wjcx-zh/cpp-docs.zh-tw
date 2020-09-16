---
title: 建立 C++ 主控台應用程式專案
description: 在 Visual Studio 中使用 Microsoft c + + 建立 Hello World 主控台應用程式。
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 333bb6ce1f3ea0db6b07d70ddd60d4a4be337abd
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686505"
---
# <a name="create-a-c-console-app-project"></a>建立 C++ 主控台應用程式專案

通常 C++ 程式設計師的起點都是 "Hello, world!" 應用程式 (在命令列上執行)。 這就是您將在此步驟 Visual Studio 中建立的。

## <a name="prerequisites"></a>先決條件

- 安裝 Visual Studio 和使用 C++ 進行桌面開發工作負載，並在您的電腦上執行。 若尚未安裝，請參閱 [Install C++ support in Visual Studio](vscpp-step-0-installation.md) (在 Visual Studio 中安裝 C++ 支援)。

## <a name="create-your-app-project"></a>建立您的應用程式專案

Visual Studio 會使用「專案」** 來組織應用程式的程式碼，並使用「解決方案」** 來組織專案。 專案包含用來建置您應用程式的所有選項、組態和規則。 它會管理所有專案檔案與任何外部檔案之間的關聯性。 若要建立您的應用程式，首先，您會建立新的專案及解決方案。

::: moniker range=">=vs-2019"

1. 在 Visual Studio 中，開啟 [檔案 **] 功能表，然後選擇 [** **新增 > 專案** ]，以開啟 [ **建立新專案** ] 對話方塊。 選取具有**c + +**、 **Windows**和**主控台**標記的**主控台應用程式**範本，然後選擇 **[下一步]**。

   ![建立新專案](media/vs2019-choose-console-app.png "開啟 [建立新專案] 對話方塊")

1. 在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 編輯方塊中，輸入*HelloWorld* 。 選擇 [ **建立** ] 以建立專案。

   ![[設定您的新專案] 對話方塊的螢幕擷取畫面，其中包含 [專案名稱] 文字欄位中的 Hello World 類型。](media/vs2019-configure-new-project-hello-world.png "命名並建立新專案")

   Visual Studio 建立新專案。 您可以新增和編輯您的原始程式碼。 根據預設，主控台應用程式範本會以 "Hello World" 應用程式填滿您的原始程式碼：

   ![IDE 中的 Hello World 專案](media/vs2019-hello-world-code.png "IDE 中的 Hello World 專案")

   當程式碼在編輯器中看起來像這樣，您就可以開始進行下一個步驟，並建立您的應用程式。

[發生問題。](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. 在 Visual Studio 中，開啟 [檔案 **] 功能表，然後選擇 [** **新增 > 專案** ]，以開啟 [ **新增專案** ] 對話方塊。

   ![開啟 [新增專案] 對話方塊](media/vscpp-file-new-project.gif "開啟 [新增專案] 對話方塊")

1. 在 [ **新增專案** ] 對話方塊中，選取 [已 **安裝的 > Visual C++** ] （如果尚未選取），然後選擇 [ **空白專案** ] 範本。 在 [ **名稱** ] 欄位中，輸入 *HelloWorld*。 選擇 **[確定]** 以建立專案。

   ![[新增專案] 對話方塊的螢幕擷取畫面，其中已安裝 > Visual C + +，並已選取並呼叫 out、[空白專案] 選項稱為 [空白]，然後在 [名稱] 文字方塊中輸入 Hellow 世界。](media/vscpp-concierge-project-name-callouts.png "命名並建立新專案")

Visual Studio 會建立新的空白專案。 您可以針對想要建立的應用程式類型進行特製化，並新增您的原始程式碼檔案。 您接下來將執行該作業。

[發生問題。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>將您的專案設為主控台應用程式

Visual Studio 可以建立適用于 Windows 和其他平臺的各種應用程式和元件。 **空白專案**範本並不是它所建立之應用程式類型的特定專案範本。 *主控台應用程式*是在主控台或命令提示字元視窗中執行的應用程式。 若要建立一個，您必須告訴 Visual Studio 建立您的應用程式以使用主控台子系統。

1. 在 Visual Studio 中，開啟 [ **專案** ] 功能表，並選擇 [ **屬性** ] 以開啟 [ **HelloWorld 屬性頁** ] 對話方塊。

1. 在 [ **屬性頁** ] 對話方塊中，選取 [設定 **屬性] > 連結器 > 系統**]，然後選擇 **子系統** 屬性旁的編輯方塊。 在出現的下拉式功能表中，選取 [ **主控台] (/subsystem：主控台) **。 選取 [確定]**** 儲存您的變更。

   ![開啟 [屬性頁] 對話方塊](media/vscpp-properties-linker-subsystem.gif "開啟 [屬性頁] 對話方塊")

Visual Studio 現在知道要建立您的專案，以在主控台視窗中執行。 接下來，您將新增原始程式碼檔案，並輸入應用程式的程式碼。

[發生問題。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>新增原始程式碼檔

1. 在 **方案總管**中，選取 HelloWorld 專案。 在功能表列上，選擇 [ **專案**]、[ **加入新專案** ]，開啟 [ **加入新專案** ] 對話方塊。

1. 在 [**加入新專案**] 對話方塊中，選取 [已**安裝**] 下方的**Visual C++** （如果尚未選取）。 在中央窗格中，選取 [ **c + + 檔案 ( .cpp) **。 將 **名稱** 變更為 *HelloWorld .cpp*。 選擇 [ **新增** ] 以關閉對話方塊並建立檔案。

   ![新增 HelloWorld 的原始程式檔](media/vscpp-add-new-item.gif "新增 HelloWorld 的原始程式檔")

Visual studio 會建立新的空白原始程式碼檔案，並在編輯器視窗中開啟該檔案，並準備好輸入您的原始程式碼。

[發生問題。](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>將程式碼加入至原始程式檔

1. 將此程式碼複製到 HelloWorld .cpp 編輯器視窗。

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   在編輯器視窗中，程式碼看起來應該像這樣：

   ![在編輯器中 Hello World 程式碼](media/vscpp-hello-world-editor.png "在編輯器中 Hello World 程式碼")

當程式碼在編輯器中看起來像這樣，您就可以開始進行下一個步驟，並建立您的應用程式。

[發生問題。](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [建立和執行 c + + 專案](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>疑難排解指南

當您建立第一個 c + + 專案時，請在此提供常見問題的解決方案。

### <a name="create-your-app-project-issues"></a>建立您的應用程式專案：問題

::: moniker range="vs-2019"

[**新增專案**] 對話方塊應會顯示具有**c + +**、 **Windows**和**主控台**標記的**主控台應用程式**範本。 如果您沒有看到它，有兩個可能的原因。 它可能會從清單中篩選出來，或可能尚未安裝。 首先，檢查範本清單頂端的 [篩選] 下拉式清單。 將它們設定為 **c + +**、 **Windows**和 **主控台**。 應該會出現 c + + **主控台應用程式** 範本;否則，就不會安裝 **使用 c + + 的桌面開發** 工作負載。

若要 **使用 c + + 安裝桌面開發**，您可以直接從 [ **新增專案** ] 對話方塊執行安裝程式。 選擇範本清單底部的 [ **安裝更多工具和功能** ] 連結，以啟動安裝程式。 如果 [ **使用者帳戶控制** ] 對話方塊要求許可權，請選擇 [ **是]**。 在安裝程式中，請確定已核取 [ **使用 c + + 的桌面開發** ] 工作負載。 然後選擇 [ **修改** ]，以更新您的 Visual Studio 安裝。

如果已經有另一個同名的專案，請為您的專案選擇另一個名稱。 或者，刪除現有的專案，然後再試一次。 若要刪除現有的專案，請刪除 [方案] 資料夾， (檔案總管中包含 *helloworld .sln* 檔案的資料夾) 。

[返回](#create-your-app-project)。

::: moniker-end

::: moniker range="vs-2017"

如果 [**新增專案**] 對話方塊未顯示 [**已安裝**] **Visual C++** 專案，則您的 Visual Studio 複本可能沒有安裝**c + +** 工作負載的桌面開發。 您可以直接從 [ **新增專案** ] 對話方塊執行安裝程式。 選擇 [ **開啟 Visual Studio 安裝程式** ] 連結，以重新開機安裝程式。 如果 [ **使用者帳戶控制** ] 對話方塊要求許可權，請選擇 [ **是]**。 如有必要，請更新安裝程式。 在安裝程式中，確定已核取 [ **使用 c + + 進行桌面開發** ] 工作負載，然後選擇 **[確定]** 以更新 Visual Studio 安裝。

::: moniker-end

::: moniker range="<=vs-2017"

如果已經有另一個同名的專案，請為您的專案選擇另一個名稱。 或者，刪除現有的專案，然後再試一次。 若要刪除現有的專案，請刪除 [方案] 資料夾， (檔案總管中包含 *helloworld .sln* 檔案的資料夾) 。

[返回](#create-your-app-project)。

### <a name="make-your-project-a-console-app-issues"></a>將您的專案設為主控台應用程式：問題

如果您看不到 [設定**屬性**] 底下列出的**連結器**，請選擇 [**取消**] 以關閉 [**屬性頁**] 對話方塊。 請先確定已在**方案總管**中選取**HelloWorld**專案，然後再試一次。 請勿在**方案總管**中選取**HelloWorld**方案或另一個專案。

下拉式清單控制項不會出現在 [ **子系統** 屬性] 編輯方塊中，直到您選取該屬性為止。 按一下 [編輯] 方塊以選取它。 或者，您可以按 **tab** 鍵迴圈流覽對話方塊控制項，直到 **子系統** 反白顯示。 選擇下拉式清單控制項，或按 **Alt + 向下** 鍵以開啟它。

[返回](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>新增原始程式碼檔：問題

如果您為原始程式碼檔提供不同的名稱，也沒關係。 不過，請勿將包含相同程式碼的多個檔案新增至您的專案。

如果您將錯誤的檔案類型新增至您的專案（例如標頭檔），請將它刪除，然後再試一次。 若要刪除檔案，請在 **方案總管**中加以選取。 然後按下 **Delete** 鍵。

[返回](#add-a-source-code-file)。

### <a name="add-code-to-the-source-file-issues"></a>將程式碼新增至原始程式檔：問題

如果您不小心關閉了 [原始程式碼檔編輯器] 視窗，您可以輕鬆地將它開啟。 若要開啟它，請按兩下 **方案總管** 視窗中的 [HelloWorld]。

如果 [原始程式碼編輯器] 的任何專案底下出現紅色波浪線，請檢查您的程式碼是否符合拼寫、標點符號和大小寫的範例。 大小寫在 c + + 程式碼中是很重要的。

[返回](#add-code-to-the-source-file)。

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
