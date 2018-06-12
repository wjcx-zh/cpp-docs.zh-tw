---
title: 使用安裝專案部署 Visual C++ 應用程式 | Microsoft Docs
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
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33332776"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>逐步解說：使用安裝專案部署 Visual C++ 應用程式
描述如何使用安裝專案部署 Visual C++ 應用程式。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   已安裝 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 的電腦。  
  
-   沒有 Visual C++ 程式庫的另一部電腦。  
  
### <a name="to-deploy-an-application-by-using-a-setup-project"></a>使用安裝專案部署應用程式  
  
1.  使用 **MFC ApplicationWizard** 來建立新的 Visual Studio 解決方案。 若要尋找精靈，請從 [新增專案] 對話方塊方塊中，展開 [Visual C++] 節點、依序選取 [MFC] 和 [MFC 應用程式]、輸入專案名稱，然後按一下 [確定]。  
  
2.  將使用中的解決方案組態變更為 [發行]。 從 [建置] 功能表，選取 [組態管理員]。 在 [組態管理員] 對話方塊中，選取 [使用中的方案組態] 下拉式清單方塊上的 [發行]。  
  
3.  按 F7 建置應用程式。 或者，在 [建置] 功能表上，按一下 [建置方案]。 這可讓安裝專案使用此 MFC 應用程式專案的輸出。  
  
4.  如果您尚未這樣做，請下載 InstallShield 限量版 (ISLE)，這免費提供給 Visual Studio 開發人員，並且會取代 Visual Studio 中的專案範本功能以進行安裝和部署。 當您連線到網際網路時，開啟 [新增專案] 對話方塊，方法是選擇功能表列上的 [檔案]、[新增]、[專案]，或以滑鼠右鍵按一下 [方案總管] 中的解決方案，然後選擇 [新增]、[新增專案]。 展開 [其他專案類型] 節點、選擇 [安裝和部署] 節點中的 [啟用 InstallShield 限量版]，並遵循顯示的指示。 在您下載、安裝和啟動 InstallShield 限量版之後，關閉 Visual Studio 並重新開啟。  
  
5.  再次開啟 [新增專案] 對話方塊、展開 [其他專案類型] 節點，然後選擇 [InstallShield 限量版] 節點中的 [InstallShield 限量版專案]。  
  
6.  遵循 InstallShield 限量版範本所建立之安裝專案的 [使用者入門] 節點上的指示，新增 Visual Studio MFC 專案的輸出參考。  
  
7.  建置安裝專案來建立安裝程式檔案 (setup.exe)。 若要這樣做，請以滑鼠右鍵按一下 [方案總管] 中的安裝專案節點，然後選取 [建置]。  
  
     InstallShield 限量版會在安裝專案樹狀結構中建立安裝檔 (根據預設，它可能位於安裝專案的 Express\SingleImage\DiskImages\DISK1 子資料夾)。  
  
8.  在沒有 Visual C++ 程式庫的第二部電腦上執行安裝程式。  
  
## <a name="see-also"></a>請參閱  
 [部署範例](../ide/deployment-examples.md)