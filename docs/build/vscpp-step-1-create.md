---
title: 建立 C++ 主控台應用程式專案
description: 在可視化工作室中使用 Microsoft C++創建 Hello World 控制台應用程式。
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 07e88da9a8a3712e1d37e319c29fd25aebce8ea7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749305"
---
# <a name="create-a-c-console-app-project"></a>建立 C++ 主控台應用程式專案

通常 C++ 程式設計師的起點都是 "Hello, world!" 應用程式 (在命令列上執行)。 這是您將在 Visual Studio 中創建的步驟。

## <a name="prerequisites"></a>Prerequisites

- 安裝 Visual Studio 和使用 C++ 進行桌面開發工作負載，並在您的電腦上執行。 若尚未安裝，請參閱 [Install C++ support in Visual Studio](vscpp-step-0-installation.md) (在 Visual Studio 中安裝 C++ 支援)。

## <a name="create-your-app-project"></a>建立您的應用程式專案

Visual Studio 會使用「專案」** 來組織應用程式的程式碼，並使用「解決方案」** 來組織專案。 專案包含用來建置您應用程式的所有選項、組態和規則。 它管理專案的所有檔和任何外部文件之間的關係。 若要建立您的應用程式，首先，您會建立新的專案及解決方案。

::: moniker range=">=vs-2019"

1. 在可視化工作室中,打開 **「檔**」功能表並選擇 **「新建>專案**」以打開「**創建新專案」** 對話方塊。 選擇具有**C++、Windows**和**主控台**標記**Windows****的主控台應用**範本,然後選擇 **「下一步**」 。。

   ![建立新專案](media/vs2019-choose-console-app.png "開啟「建立新項目」對話框")

1. 在「**設定新項目**」對話框中,在 **「專案名稱**編輯」框中輸入*HelloWorld。* 選擇 **「建立**」 以建立專案。

   ![具建立新項目](media/vs2019-configure-new-project-hello-world.png "具建立新項目")

   可視化工作室創建一個新專案。 它可供您添加和編輯原始碼。 預設情況下,主控台應用範本使用「Hello World」應用填充源代碼:

   ![你好世界專案在IDE](media/vs2019-hello-world-code.png "你好世界專案在IDE")

   當編輯器中的代碼如下所示時,您可以繼續下一步並構建應用。

[發生問題。](#create-your-app-project-issues)

::: moniker-end

::: moniker range="<=vs-2017"

1. 在可視化工作室中,打開 **「檔**」功能表並選擇 **「新專案>專案**以打開 **」新專案**「對話框。

   ![開啟 [新增專案] 對話方塊](media/vscpp-file-new-project.gif "開啟 [新增專案] 對話方塊")

1. 在"**新項目"** 對話方塊中,選擇 **「 已安裝> 可視化 C++(** 如果尚未選中),然後選擇 **「空專案**」樣本。 在 **「名稱」** 欄位中,輸入*HelloWorld*。 選擇 **「確定」** 以建立專案。

   ![具建立新項目](media/vscpp-concierge-project-name-callouts.png "具建立新項目")

可視化工作室創建一個新的空專案。 它可供您專門用於要創建的應用類型並添加原始程式碼檔。 您接下來將執行該作業。

[發生問題。](#create-your-app-project-issues)

## <a name="make-your-project-a-console-app"></a>使項目成為主控台應用

Visual Studio 可以為 Windows 和其他平台創建各種應用和元件。 **空專案**模板不特定於它創建的應用類型。 *控制台應用*是在主控台或命令提示視窗中運行的應用。 要建立一個,您必須告訴 Visual Studio 構建應用以使用主控台子系統。

1. 在可視化工作室中,打開 **「專案」** 功能表並選擇 **「屬性**」以打開**HelloWorld 屬性頁**對話框。

1. 在 **「屬性頁」** 對話方塊中,選擇 **「設定屬性> 連結器>系統**,然後選擇**子系統**屬性旁邊的編輯框。 在顯示的下拉菜單中,選擇**主控台(/SUBSYSTEM:CONSOLE)。** 選取 [確定]**** 儲存您的變更。

   ![開啟屬性頁對話框](media/vscpp-properties-linker-subsystem.gif "開啟屬性頁對話框")

Visual Studio 現在知道要構建要在主控台視窗中運行的專案。 接下來,您將添加一個原始程式碼檔,並輸入應用的代碼。

[發生問題。](#make-your-project-a-console-app-issues)

## <a name="add-a-source-code-file"></a>新增原始碼檔案

1. 在**解決方案資源管理器中**,選擇HelloWorld專案。 在選單列上,選擇 **「專案**」,**添加新專案**以打開「**新增新專案」** 對話方塊。

1. 在「**添加新項目」** 對話方塊中,如果尚未選中「已安裝」,則在「**已安裝**」下選擇 **「可視C++」。** 在中心窗格中,選擇**C++檔 (.cpp)**。 將**名稱**變更為*HelloWorld.cpp*。 選擇 **「新增」** 以關閉對話框並建立檔案。

   ![為 HelloWorld.cpp 添加源檔](media/vscpp-add-new-item.gif "為 HelloWorld.cpp 添加源檔")

Visual Studio 會建立一個新的空源代碼檔,並在編輯器視窗中打開該檔,以便輸入原始碼。

[發生問題。](#add-a-source-code-file-issues)

## <a name="add-code-to-the-source-file"></a>新增程式碼到源碼

1. 將此代碼複製到 HelloWorld.cpp 編輯器視窗中。

   ```cpp
   #include <iostream>

   int main()
   {
       std::cout << "Hello, world!" << std::endl;
       return 0;
   }
   ```

   代碼應在編輯器視窗中如下所示:

   ![你好世界代碼在編輯器](media/vscpp-hello-world-editor.png "你好世界代碼在編輯器")

當編輯器中的代碼如下所示時,您可以繼續下一步並構建應用。

[發生問題。](#add-a-source-code-file-issues)

::: moniker-end

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [產生並執行C++專案](vscpp-step-2-build.md)

## <a name="troubleshooting-guide"></a>疑難排解指南

創建第一個C++專案時,請在此處尋求常見問題的解決方案。

### <a name="create-your-app-project-issues"></a>建立應用項目:問題

::: moniker range="vs-2019"

"**新項目**"對話框應顯示具有**C++、Windows**和**C++****控制台標記的****控制台應用**範本。 如果您看不到它,則有兩個可能的原因。 它可能從清單中篩選出來,或者可能未安裝。 首先,檢查範本列表頂部的篩選器下拉清單。 將它們設定為**C++、Windows**和**Windows****主控台**。 應顯示C++**控制台應用**範本;否則,未安裝**具有C++工作負載的桌面開發**。

要使用 C++ 安裝**桌面開發**,可以從 **「新專案」** 對話方塊中直接執行安裝程式。 在樣本清單底部選擇 **「安裝更多工具和功能**」連結以啟動安裝程式。 如果**使用者帳戶控制**對話方塊請求權限,請選擇 **「 是**」。 在安裝程式中,請確保選擇**中具有 C++工作負載的桌面開發**。 然後選擇 **「修改」** 以更新可視化工作室安裝。

如果另一個具有相同名稱的專案已存在,請為項目選擇另一個名稱。 或者,刪除現有項目,然後重試。 要刪除現有專案,請刪除檔案資源管理器中的解決方案資料夾(包含*helloworld.sln*檔案的資料夾)。

[回去](#create-your-app-project)吧。

::: moniker-end

::: moniker range="vs-2017"

如果 **「新項目」** 對話框未在 **「已安裝**」下顯示 **「視覺C++」** 項目,則 Visual Studio 的副本可能沒有安裝C++工作負載的**桌面開發**。 您可以直接從 **「新專案」** 對話框執行安裝程式。 選擇 **「打開視覺化工作室安裝程式」** 連結以重新啟動安裝程式。 如果**使用者帳戶控制**對話方塊請求權限,請選擇 **「 是**」。 如有必要,更新安裝程式。 在安裝程式中,請確保選中**具有C++工作負載的桌面開發**,然後選擇 **「確定」** 以更新 Visual Studio 安裝。

::: moniker-end

::: moniker range="<=vs-2017"

如果另一個具有相同名稱的專案已存在,請為項目選擇另一個名稱。 或者,刪除現有項目,然後重試。 要刪除現有專案,請刪除檔案資源管理器中的解決方案資料夾(包含*helloworld.sln*檔案的資料夾)。

[回去](#create-your-app-project)吧。

### <a name="make-your-project-a-console-app-issues"></a>使項目成為主控台應用:問題

如果未在**設定屬性**下列出**連結器**,請選擇 **「取消」** 以關閉**屬性頁**對話框。 在重試之前,請確保**HelloWorld**專案在**解決方案資源管理器**中被選中。 不要在**解決方案資源管理器**中選擇**HelloWorld**解決方案或其他專案。

在選擇該屬性之前,下拉控制件不會顯示在**SubSystem**屬性編輯框中。 按一下編輯框以選擇它。 或者,您可以按**Tab**以循環瀏覽對話框控制項,直到**突顯子系統**。 選擇下拉控制件或按 **「向下」** 將其打開。

[回去](#make-your-project-a-console-app)

### <a name="add-a-source-code-file-issues"></a>新增原始碼檔:問題

如果給原始碼檔指定不同的名稱,則沒關係。 但是,不要向專案添加多個包含相同代碼的檔。

如果將錯誤的檔案類型添加到專案(如頭檔)中,請將其刪除,然後重試。 要刪除該檔,請在**解決方案資源管理員**中選擇該檔。 然後按 **「刪除**」鍵。

[回去](#add-a-source-code-file)吧。

### <a name="add-code-to-the-source-file-issues"></a>將代碼加入來源檔案:問題

如果意外關閉了原始碼檔編輯器視窗,則可以輕鬆地再次打開它。 要打開它,請在**解決方案資源管理器**視窗中按兩下 HelloWorld.cpp。

如果原始碼編輯器中的任何內容下出現紅色波浪,請檢查代碼是否與拼寫、標點符號和大小寫中的範例匹配。 案例在C++代碼中非常重要。

[回去](#add-code-to-the-source-file)吧。

::: moniker-end

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
