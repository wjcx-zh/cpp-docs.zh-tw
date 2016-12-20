---
title: "MSBuild 錯誤 MSB3841 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.ResolveSDKReference.InvalidDependencyInPlatform"
ms.assetid: 80ed22a1-bd62-4ace-892f-6b6009dff8e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3841
**MSB3841：SDK "{1}" 相依於 SDK "{0}"，這與以平台版本 "{2}" 為目標的專案不相容。**  
  
 當您的專案具有與您專案的目標平台不相容的相依性時，MSBuild 會產生此錯誤。  依賴不相容的相依性可能會導致在執行階段發生失敗或未預期的應用程式行為  
  
### 更正專案參考的這個錯誤  
  
1.  以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 市集專案為目標的 Visual Basic、C\#、C\+\+ 和 JavaScript 專案無法參考以 [!INCLUDE[win8](../build/includes/win8_md.md)] 為目標的 C\+\+ Windows 市集專案，因為這會造成執行階段問題。  如果您應用程式中有任何專案是以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 為目標，而且您的應用程式是由 C\+\+ Windows 市集專案所組成，您必須執行下列步驟：  
  
2.  將您的應用程式中所有專案的目標重定為 [!INCLUDE[win81](../misc/includes/win81_md.md)]。  在您的應用程式中的每個專案上按一下滑鼠右鍵、選取 \[**將目標重定為 Windows 8.1**\] 命令，然後按一下 \[**檢閱專案和方案變更**\] 對話方塊上的 \[**確定**\]，即可執行這項操作。  
  
3.  在相依於 C\+\+ Windows 市集專案的每個 Visual Basic、C\# 和 JavaScript 專案上按一下滑鼠右鍵，選擇 \[**加入參考**\]、移至 \[**Windows**\] 索引標籤，然後在 \[**擴充功能**\] 子索引標籤上，取消核取 \[**Microsoft Visual C\+\+ Runtime Package v11.0**\] 並檢查 \[**Microsoft Visual C\+\+ Runtime Package v12.0**\]，然後按一下 \[**確定**\]。  
  
4.  以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 為目標的 Visual Basic、C\# 和 JavaScript Windows 市集專案可以參考以 [!INCLUDE[win8](../build/includes/win8_md.md)] 為目標的 Visual Basic 和 C\# Windows 市集專案，前提是 [!INCLUDE[win8](../build/includes/win8_md.md)] 市集專案不使用已在 [!INCLUDE[win81](../misc/includes/win81_md.md)] 中被取代的 API。  請參閱[將 Windows 8 應用程式移轉至 Windows 8.1 Preview](http://msdn.microsoft.com/library/windows/apps/dn263113.aspx)，以確定 [!INCLUDE[win8](../build/includes/win8_md.md)] 市集專案在從 [!INCLUDE[win81](../misc/includes/win81_md.md)] 專案進行參考時是否繼續如預期般運作。  
  
     [!INCLUDE[win8](../build/includes/win8_md.md)] 市集專案無法相依於以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 為目標的 Windows 市集專案或二進位檔。  
  
### 更正 Extension SDK 參考的這個錯誤  
  
1.  以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 為目標的 Visual Basic、C\#、C\+\+ 和 JavaScript Windows 市集專案無法參考相依於 Microsoft Visual C\+\+ Runtime Package v11.0 的擴充功能 SKD，因為這會造成執行階段問題。  您可以找出擴充功能 SDK 是否相依於 Microsoft Visual C\+\+ Runtime Package v11.0，其作法是建立新的 C\# Windows 市集專案，在專案上按一下滑鼠右鍵並選擇 \[**加入參考**\]，移至 \[**Windows**\] 索引標籤，然後移至 \[**擴充功能**\] 子索引標籤，選取擴充功能 SDK 並查看 \[**參考管理員**\] 的右窗格是否列出 \[**Microsoft.VCLibs，版本 \= 11.0**\] 做為相依性。  
  
     以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 為目標的 Visual Basic、C\# 和 JavaScript Windows 市集專案可以參考不相依於 Microsoft Visual C\+\+ Runtime Package v11.0 的擴充功能 SKD，前提是這些擴充功能 SKD 不使用已在 [!INCLUDE[win81](../misc/includes/win81_md.md)] 中被取代的 API。  請檢查擴充功能 SDK 廠商網站，以確定是否可由以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 為目標的市集專案參考。  
  
     如果您判定不支援您的應用程式所參考的擴充功能 SDK，則需要執行下列步驟：  
  
2.  查看造成錯誤的專案名稱。  您的專案的目標平台加註在專案名稱旁邊的括號中。  例如，**MyProjectName \(Windows 8.1\)** 表示您的專案 MyProjectName 的目標平台版本為 [!INCLUDE[win81](../misc/includes/win81_md.md)]。  
  
3.  移至擁有不受支援之擴充功能 SDK 的廠商網站，並安裝相依性與您專案的目標平台版本相容的擴充功能 SDK 版本。  
  
4.  如果您先前安裝的擴充功能 SDK 具有其他擴充功能 SDK 的相依性，請移至擁有相依性的廠商網站，並安裝與您專案的目標平台版本相容的這些相依性版本。  
  
    > [!NOTE]
    >  如果您的專案是以 [!INCLUDE[win81](../misc/includes/win81_md.md)] 為目標且先前安裝的擴充功能 SDK 相依於 Microsoft Visual C\+\+ Runtime Package，則與 Windows 8.1 相容的 Microsoft Visual C\+\+ Runtime Package 版本為 v12.0 並隨著 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 一起安裝。  
  
    > [!NOTE]
    >  若要找出先前安裝的擴充功能 SDK 是否具有其他擴充功能 SDK 的相依性，請重新啟動 Visual Studio，建立新的 C\# Windows 市集專案，以滑鼠右鍵按一下專案並選擇 \[**加入參考**\]，移至 \[**Windows**\] 索引標籤，再移至 \[**擴充功能**\] 子索引標籤，選取擴充功能 SDK 並 \[**參考管理員**\] 的查看右窗格。  如果有相依性，則會在那裡列出。  
  
5.  重新啟動 Visual Studio，然後開啟您的應用程式。  
  
6.  在造成錯誤的專案上按一下滑鼠右鍵，然後選擇 \[**加入參考**\] \(適用於 Visual Basic、C\# 或 JavaScript 專案\) 或 \[**參考**\] \(適用於 C\+\+ 專案\)。  在 C\+\+ 專案中，接著按一下 \[加入新參考\] 按鈕。  
  
7.  按一下 \[**Windows**\] 索引標籤，然後按一下 \[**擴充功能**\] 子索引標籤。  取消選取舊擴充功能 SDK 旁邊的核取方塊，然後選取新擴充功能 SDK 旁邊的核取方塊。  按一下 \[**確定**\]。