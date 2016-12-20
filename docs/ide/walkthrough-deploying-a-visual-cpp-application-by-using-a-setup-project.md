---
title: "逐步解說：使用安裝專案部署 Visual C++ 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Visual C++ 的部署"
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：使用安裝專案部署 Visual C++ 應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

說明如何使用安裝專案部署 Visual C\+\+ 應用程式。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   已安裝 [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] 的電腦。  
  
-   另一部沒有 Visual C\+\+ 程式庫的電腦。  
  
### 若要使用安裝專案部署應用程式  
  
1.  使用 \[**MFC 應用程式精靈**\] 建立新的 Visual Studio 方案。  若要尋找精靈，請從 \[**新增專案**\] 對話方塊展開 \[**Visual C\+\+**\] 節點，依序選取 \[**MFC**\]、\[**MFC 應用程式**\]，輸入專案名稱，然後按一下 \[**確定**\]。  
  
2.  將使用中的方案組態變更為 \[**發行**\]。  從 \[**建置**\] 功能表中，選取 \[**組態管理員**\]。  從 \[**組態管理員**\] 對話方塊中，選取 \[**使用中的方案組態**\] 下拉式方塊中的 \[**發行**\]。  
  
3.  請按 F7 建置應用程式。  或者，在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  這可讓安裝專案使用這個 MFC 應用程式專案輸出。  
  
4.  如果您還沒這麼做，下載 InstallShield Limited Edition \(小島\)，在 Visual Studio 開發人員可用的並取代專案範本功能在 Visual Studio 的安裝和部署的。  當您連接到網際網路時，開啟 \[**新的專案**\] 對話方塊中選取 \[**檔案**\]\]，則 \[**新增**\]，請在功能表列上的 \[**專案**\] ，或是以滑鼠右鍵按一下 \[**方案總管**\] 中的方案、選取 \[**加入**\]\]，則 \[**新的專案…**\]。  展開 \[**其他的專案類型**\] 節點，選取 \[**安裝和部署**\] 節點的 \[**啟用 InstallShield Limited Edition**\] \]，然後遵循中的指示。  在您下載，安裝和啟動的 InstallShield Limited Edition，請結束 Visual Studio 並重新開啟。  
  
5.  重新開啟 \[**新的專案**\] 對話方塊中，展開 \[**其他的專案類型**\] 節點，然後選擇 \[**InstallShield Limited Edition**\] 節點中的 \[**InstallShield Limited Edition 專案**\] 。  
  
6.  依照 InstallShield Limited Edition 範本所建立的安裝專案的 \[**啟動**\] 節點中指示加入至 Visual Studio MFC 專案的專案輸出參考。  
  
7.  建立安裝專案建立安裝程式檔 \(setup.exe\)。  若要這麼做，請以滑鼠右鍵按一下 \[**方案總管**\] 中的安裝專案節點並選取 \[**組建**\]。  
  
     InstallShield Limited Edition 建立安裝專案樹狀結構中的設定檔 \(根據預設，它可能位於安裝專案的 Express\\SingleImage\\DiskImages\\DISK1 子資料夾\)。  
  
8.  會在沒有 Visual C\+\+ 程式庫的第二部電腦上執行安裝程式。  
  
## 請參閱  
 [部署範例](../ide/deployment-examples.md)