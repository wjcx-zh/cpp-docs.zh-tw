---
title: 使用安裝專案部署 Visual c + + 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 454507a3a3f33b43af0e50c25dab6703aa75a56b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>逐步解說：使用安裝專案部署 Visual C++ 應用程式
描述如何使用安裝專案部署 Visual c + + 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   與電腦[!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)]安裝。  
  
-   額外的電腦未安裝 Visual c + + 程式庫。  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>若要使用安裝專案部署應用程式  
  
1.  使用**MFC ApplicationWizard**來建立新的 Visual Studio 方案。 若要尋找精靈，從**新專案**對話方塊方塊中，展開  **Visual c + +** 節點中，選取**MFC**，選取**MFC 應用程式**，輸入為專案命名，然後按一下**確定**。  
  
2.  將使用中的方案組態變更為**發行**。 從**建置**功能表上，選取**Configuration Manger**。 從**Configuration Manager**對話方塊中，選取**發行**從**現用方案組態**下拉式清單方塊。  
  
3.  按下 f7 鍵，建置應用程式。 或在**建置**功能表上，按一下 **建置方案**。 這可讓安裝專案中，使用此 MFC 應用程式專案的輸出。  
  
4.  如果您尚未這樣做，請下載 InstallShield Limited Edition (ISLE)，這是免費的 Visual Studio 開發人員，並取代的專案範本在 Visual Studio 中安裝和部署的功能。 當您連線到網際網路時，開啟**新專案**對話方塊中，選擇**檔案**，**新增**，**專案**功能表列，或以滑鼠右鍵按一下方案中的**方案總管 中**，然後選擇**新增**，**新專案**。 展開**其他專案類型** 節點，選擇**啟用 InstallShield 限量版**中**安裝和部署** 節點，並依照所顯示的指示。 一旦您已下載、 安裝並啟動 InstallShield 限量版，請關閉 Visual Studio 並重新開啟它。  
  
5.  開啟**新專案**對話方塊同樣地，依序展開**其他專案類型**] 節點，然後選擇 [ **InstallShield 限量版專案**中**InstallShield Limited Edition**節點。  
  
6.  遵循指示**入門**InstallShield 限量版範本，若要加入您的 Visual Studio MFC 專案輸出參考所建立之安裝專案節點。  
  
7.  建置安裝專案來建立安裝程式檔案 (setup.exe)。 若要這樣做，請以滑鼠右鍵按一下安裝程式的專案節點中**方案總管 中**選取**建置**。  
  
     InstallShield Limited Edition 建立安裝專案樹狀結構中的安裝檔 （根據預設，它可能位於安裝專案的 Express\SingleImage\DiskImages\DISK1 子資料夾）。  
  
8.  在沒有 Visual c + + 程式庫第二部電腦上執行安裝程式。  
  
## <a name="see-also"></a>另請參閱  
 [部署範例](../ide/deployment-examples.md)