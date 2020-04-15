---
title: 逐步解說：部署程式 (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: eacbcef82f240589e71b59f80d8e19602ceda869
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365013"
---
# <a name="walkthrough-deploying-your-program-c"></a>逐步解說：部署程式 (C++)

現在您已經透過完成先前的相關逐步解說建立您的應用程式，最後一個步驟要建立安裝程式，讓其他使用者可以將程式安裝在電腦上。 針對安裝程式，您需要將新的專案新增至現有方案中。 這個新專案的輸出是 setup.exe 檔案，這個檔案會將您的應用程式安裝在另一部電腦上。

本逐步解說示範如何使用 Windows Installer 部署您的應用程式。 您也可以使用 ClickOnce 部署應用程式。 如需詳細資訊，請參閱 [ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md)。 如需部署的一般詳細資訊，請參閱[部署應用程式、服務和元件](/visualstudio/deployment/deploying-applications-services-and-components)。

## <a name="prerequisites"></a>Prerequisites

- 本逐步解說假設您已了解 C++ 語言的基本概念。

- 也會假設您已完成先前列於[使用 Visual Studio IDE 進行 C++ 桌面程式開發](using-the-visual-studio-ide-for-cpp-desktop-development.md)中的相關逐步解說。

- 這個逐步解說無法在 Visual Studio Express Edition 中完成。

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>安裝 Visual Studio 安裝程式和部署專案範本

本節中的步驟視您已安裝 Visual Studio 版本而有所不同。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

<!-- markdownlint-disable MD034 -->

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>安裝 Visual Studio 2019 安裝程式和部署專案範本

1. 如果您尚未這樣做,請下載 Microsoft 視覺化工作室安裝程式專案擴展。 延伸模組是免費提供給 Visual Studio 開發人員使用，並可將安裝和部署專案範本的功能新增至 Visual Studio。 連接到網際網路時,在可視化工作室中,選擇**延伸** > **管理擴展**。 選取 [延伸模組和更新]**** 對話方塊下方的 [線上]**** 索引標籤，然後在搜尋方塊中鍵入「Microsoft Visual Studio 安裝程式專案」**。 按 **Enter**，選取 [Microsoft Visual Studio \<版本> 安裝程式專案]****，然後按一下 [下載]****。 選擇執行並安裝延伸模組，然後重新啟動 Visual Studio。

1. 在 Visual Studio 功能表列上，選擇 [檔案]** [最近使用的專案和方案]** > ****，然後選擇重新開啟專案。

1. 在選單列上,選擇 **「檔案** > **新專案** > **」以**開啟「**建立新項目**」 對話方塊。 在搜尋方塊中，鍵入 [安裝]，然後從結果清單中選擇 [安裝專案]****。

1. 在 [名稱]**** 方塊中，輸入安裝專案的名稱。 在 [方案]**** 下拉式清單中，選取 [新增至方案]****。 選擇 [確定]**** 按鈕以建立安裝專案。 編輯器視窗中隨即開啟 [File Assistant (ProjectName)] \(檔案小幫手 (ProjectName)\)**** 索引標籤。

1. 以滑鼠右鍵按一下 [應用程式資料夾]**** 節點，然後選取 [新增]**[專案輸出]** > **** 以開啟 [新增專案輸出群組]**** 對話方塊。

1. 在對話方塊中選取 [主要輸出]****，然後按一下 [確定]****。 隨即顯示新項目，名稱為 [Primary Output from Game (Active)] \(遊戲 (使用中) 的主要輸出\)****。

1. 選取 [Primary Output from Game (Active)] \(遊戲 (使用中) 的主要輸出\)**** 項目，再按一下滑鼠右鍵，然後選擇 [Create Shortcut to Primary Output from Game (Active)] \(建立遊戲 (使用中) 的主要輸出捷徑\)****。 隨即顯示新項目，名稱為 [Shortcut to Primary Output from Game (Active)] \(遊戲 (使用中) 的主要輸出捷徑\)****。

1. 將捷徑項目重新命名為「遊戲」**，然後將項目拖曳至視窗左側的 [使用者的程式功能表]**** 節點。

1. 在 [方案總管]**** 中，選取 [遊戲安裝程式]**** 專案，然後選擇 [檢視]** [屬性視窗]** > **** 或按 **F4**，以開啟 [屬性]**** 視窗。

1. 指定您想要在安裝程式中顯示的其他詳細資料。  例如,對**製造商**使用*Contoso,***對產品名稱***使用遊戲安裝程式*,對**支援網址**使用*\:Hs /www.contoso.com* 。

1. 在功能表列上,選擇 **「生成** > **配置管理員**」。 在 [專案]**** 資料表的 [建置]**** 資料行下方，核取 [遊戲安裝程式]**** 的方塊。 按一下 [關閉]  。

1. 在功能表列上，選擇 [建置]**[建置方案]** > **** 以建置遊戲專案和遊戲安裝程式專案。

1. 在方案資料夾中，找出從 [遊戲安裝程式] 專案建置的 setup.exe 程式，然後加以執行，將遊戲應用程式安裝在您電腦上。 您可以複製這個檔案 (和 GameInstaller.msi 檔案)，在另一部電腦上安裝應用程式及其必要的程式庫檔案。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>安裝 Visual Studio 2017 及更早版本的安裝程式和部署專案範本

1. 當您已連線到網際網路時，請在 Visual Studio 中選擇 [工具]**[延伸模組和更新]** > ****。

1. 選取 [延伸模組和更新]**** 下方的 [線上]**** 索引標籤，然後在搜尋方塊中鍵入「Microsoft Visual Studio 安裝程式專案」**。 按 **Enter**，選取 [Microsoft Visual Studio \<版本> 安裝程式專案]****，然後按一下 [下載]****。

1. 選擇安裝延伸模組，然後重新啟動 Visual Studio。

1. 在功能表列上，選擇 [檔案]**[最近使用的專案和方案]** > ****，然後選擇 [遊戲]**** 方案來重新開啟。

### <a name="to-create-a-setup-project-and-install-your-program"></a>若要建立安裝專案並安裝您的程式

1. 將使用中的方案組態變更為 [發行]。 在功能表列上,選擇 **「生成** > **配置管理員**」。 在 [組態管理員]**** 對話方塊中，選取 [使用中的方案組態]**** 下拉式清單上的 [發行]****。 選擇 [關閉]**** 按鈕以儲存組態。

1. 在功能表列上，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [新增專案]**** 對話方塊。

1. 在對話框的左方窗格中,展開 **「已安裝** > **的其他項目類型」** 節點,然後選擇**視覺化工作室安裝程式**。 在中間窗格中，選取 [安裝專案]****。

1. 在 [名稱]**** 方塊中，輸入安裝專案的名稱。 在這個範例中，請輸入*遊戲安裝程式*。 在 [方案]**** 下拉式清單中，選取 [新增至方案]****。 選擇 [確定]**** 按鈕以建立安裝專案。 [File Assistant (Game Installer)] \(檔案小幫手 (遊戲安裝程式)\)**** 索引標籤隨即在編輯器視窗中開啟。

1. 以滑鼠右鍵按一下 [應用程式資料夾]**** 節點，然後選取 [新增]**[專案輸出]** > **** 以開啟 [新增專案輸出群組]**** 對話方塊。

1. 在對話方塊中選取 [主要輸出]****，然後按一下 [確定]****。 隨即顯示新項目，名稱為 [Primary Output from Game (Active)] \(遊戲 (使用中) 的主要輸出\)****。

1. 選取 [Primary Output from Game (Active)] \(遊戲 (使用中) 的主要輸出\)**** 項目，再按一下滑鼠右鍵，然後選擇 [Create Shortcut to Primary Output from Game (Active)] \(建立遊戲 (使用中) 的主要輸出捷徑\)****。 隨即顯示新項目，名稱為 [Shortcut to Primary Output from Game (Active)] \(遊戲 (使用中) 的主要輸出捷徑\)****。

1. 將捷徑項目重新命名為「遊戲」**，然後將項目拖曳至視窗左側的 [使用者的程式功能表]**** 節點。

1. 在 [方案總管]**** 中，選取 [遊戲安裝程式]**** 專案，然後選擇 [檢視]** [屬性視窗]** > **** 或按 **F4**，以開啟 [屬性]**** 視窗。

1. 指定您想要在安裝程式中顯示的其他詳細資料。  例如,對**製造商**使用*Contoso,***對產品名稱***使用遊戲安裝程式*,對**支援網址**使用*\:Hs /www.contoso.com* 。

1. 在功能表列上,選擇 **「生成** > **配置管理員**」。 在 [專案]**** 資料表的 [建置]**** 資料行下方，核取 [遊戲安裝程式]**** 的方塊。 按一下 [關閉]  。

1. 在功能表列上，選擇 [建置]**[建置方案]** > **** 以建置遊戲專案和遊戲安裝程式專案。

1. 在方案資料夾中，找出從 [遊戲安裝程式] 專案建置的 setup.exe 程式，然後加以執行，將遊戲應用程式安裝在您電腦上。 您可以複製這個檔案 (和 GameInstaller.msi 檔案)，在另一部電腦上安裝應用程式及其必要的程式庫檔案。

::: moniker-end

## <a name="next-steps"></a>後續步驟

**上一步：** [逐步解說：偵錯專案 (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>另請參閱

[C++語言參考](../cpp/cpp-language-reference.md)<br/>
[專案和建置系統](../build/projects-and-build-systems-cpp.md)<br/>
[部署桌面應用程式](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>
