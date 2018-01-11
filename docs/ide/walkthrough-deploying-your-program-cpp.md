---
title: "逐步解說： 部署程式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce59dc7b767c8ff8e988ac7a765d3bb5f1cdfffc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-deploying-your-program-c"></a>逐步解說：部署程式 (C++)
現在，您已建立您的應用程式所完成的稍早相關逐步解說，列出的[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)，最後一個步驟是建立安裝程式，如此當其他使用者安裝程式在其電腦上。 若要完成這項工作，您需要將新的專案加入至現有方案中。 這個新專案的輸出是 setup.exe 檔案，這個檔案會將您的應用程式安裝在另一部電腦上。  
  
 本逐步解說示範如何使用 Windows Installer 部署您的應用程式。 您也可以使用 ClickOnce 部署應用程式。 如需詳細資訊，請參閱 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)。 如需有關部署一般情況下，請參閱[部署應用程式、 服務和元件](/visualstudio/deployment/deploying-applications-services-and-components)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   本逐步解說假設您已了解 C++ 語言的基本概念。  
  
-   它也會假設您已完成的稍早相關逐步解說中所列[使用 c + + 桌面開發的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
-   這個逐步解說無法在 Visual Studio 的 Express 版本中完成。  
  
-   如果您還沒有完成這部分，請下載 InstallShield Limited Edition (ISLE)，如本文稍後的步驟所述。 ISLE 免費提供給 Visual Studio 開發人員使用，可以取代舊版 Visual Studio 安裝和部署專案範本中的功能。  
  
### <a name="to-install-the-isle-setup-and-deployment-project-template"></a>若要安裝 ISLE 安裝程式並部署專案範本  
  
1.  當您連接到網際網路，請在功能表列上選擇**檔案**，**新增**，**專案**開啟**新專案** 對話方塊。  
  
2.  在對話方塊的左窗格中，依序展開**已安裝**，**範本**，和**其他專案類型**節點，然後選取**安裝和部署**. 在中央窗格中，選取**啟用 InstallShield 限量版**，然後選擇 [**確定**] 按鈕。  
  
3.  遵循指示安裝 InstallShield Limited Edition for Visual Studio (ISLE)。  
  
4.  在您下載、安裝和啟動 ISLE 之後，關閉 Visual Studio 並重新開啟。  
  
5.  在功能表列上選擇 **檔案**，**最近使用的專案和方案**，然後選擇 **遊戲**將它重新開啟方案。  
  
### <a name="to-create-a-setup-project-and-install-your-program"></a>若要建立安裝專案並安裝您的程式  
  
1.  將使用中的方案組態變更為 [發行]。 在功能表列上，選擇 [ **建置**]、[ **組態管理員**]。 在**Configuration Manager**對話方塊**現用方案組態**下拉式清單中，選取**發行**。 選擇**關閉**按鈕以儲存設定。  
  
2.  在功能表列上選擇 [**檔案**，**新增**，**專案**開啟**新專案**] 對話方塊。  
  
3.  在對話方塊的左窗格中，依序展開**已安裝**，**範本**，和**其他專案類型**節點，然後選取**安裝和部署**. 在中央窗格中，選取**InstallShield 限量版專案**。  
  
4.  輸入安裝專案中的名稱**名稱**方塊。 針對此範例中，輸入**遊戲安裝程式**。 在**方案**下拉式清單中，選取**將加入至方案**。 選擇**確定**按鈕以建立安裝專案。 A**專案助理 （遊戲安裝程式）**索引標籤會開啟編輯器視窗中。  
  
5.  在底部**專案助理 （遊戲安裝程式）**索引標籤上，選擇**應用程式資訊**連結。  
  
6.  在**應用程式資訊**頁面上，指定您的公司名稱，您想要在安裝程式會出現。 您可以使用您自己的公司名稱，或針對此範例中，使用**Contoso**。 指定您的應用程式的名稱。在此範例中，指定**遊戲**。 指定您公司的網址，或為此範例中，使用**http://www.contoso.com**。  
  
7.  在底部**專案助理 （遊戲安裝程式）**索引標籤上，選擇**安裝會談**連結。  
  
8.  在**安裝會談**頁面的 **您想要顯示授權合約對話方塊**，選取**否**選項按鈕。 在下**您是否要提示使用者輸入他們的公司名稱和使用者名稱**，選取**否**選項按鈕。  
  
9. 在**方案總管] 中**，依序展開**遊戲安裝程式**專案中，展開 [ **Organize Your Setup**節點，然後再開啟**的一般資訊**頁面。  
  
10. 在**的一般資訊 （遊戲安裝程式）**在編輯器視窗索引標籤上，指定**標記建立者 ID**，例如**regid.2012-12.com.contoso**。  
  
11. 在**方案總管] 中**下**遊戲安裝程式**專案中，展開 [ **Specify Application Data**節點，然後再開啟**檔案**頁面。  
  
12. 在**檔案 （遊戲安裝程式）**索引標籤的 [編輯器] 視窗底下**來源電腦的檔案**，開啟捷徑功能表**遊戲的主要輸出**選擇**複製**。  
  
13. 開啟快顯功能表底下空間中**名稱**中的資料行**目的電腦的檔案**，然後選擇 **貼上**。 新項目的名稱**遊戲.主要輸出**隨即出現。  
  
14. 在**方案總管 中**下**Specify Application Data**節點，開啟**可轉散發套件**頁面。  
  
15. 在**可轉散發套件 （遊戲安裝程式）**  索引標籤，在編輯器視窗中，選取**Visual c + + 11.0 CRT (x86)**核取方塊。  
  
16. 在功能表列上選擇 **建置**，**建置方案**建置 遊戲 專案和遊戲安裝程式專案。  
  
17. 在方案資料夾中，找出從 [遊戲安裝程式] 專案建置的 setup.exe 程式，然後加以執行，將遊戲應用程式安裝在您電腦上。 您可以複製這個檔案，在另一部電腦上安裝應用程式及其必要的程式庫檔案。  
  
18. 您可以設定安裝專案中的許多選項來符合您的需求。 如需詳細資訊，在**方案總管 中**下**遊戲安裝程式**專案中，開啟**入門**頁面，然後選擇 F1 鍵開啟 ISLE help library。  
  
## <a name="next-steps"></a>後續步驟  
 **上一步：** [逐步解說： 偵錯專案 （c + +）](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [建置 C/C++ 程式](../build/building-c-cpp-programs.md)  
 [部署桌面應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)