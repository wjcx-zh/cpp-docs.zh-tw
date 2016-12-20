---
title: "How to: Add MFC Support to Resource Script Files | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.add.MFC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rc files, adding MFC support"
  - ".rc files, adding MFC support"
  - "MFC, adding support to resource scripts files"
  - "resource script files, adding MFC support"
ms.assetid: 599dfe9d-ad26-4e34-899c-49b56599e37f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add MFC Support to Resource Script Files
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一般來說，當您使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)為 Windows 建置 MFC 應用程式時，精靈會產生一組基本的檔案 \(包括資源指令碼 \(.rc\) 檔\)，其中包含 Microsoft Foundation Class \(MFC\) 的核心功能。  不過，如果您要為不以 MFC 為基礎的 Windows 應用程式編輯 .rc 檔，則無法使用 MFC 架構的下列特定功能：  
  
-   MFC 程式碼精靈 \(先前稱為「[MFC ClassWizard](http://msdn.microsoft.com/zh-tw/98dc2434-ba93-4e0b-b084-1a4bc26cdf1e)」\)  
  
-   功能表提示字串  
  
-   下拉式方塊控制項的清單內容  
  
-   ActiveX 控制項裝載  
  
 不過，您可以將 MFC 支援加入至沒有該支援的現有 .rc 檔。  
  
### 將 MFC 支援加入至 .rc 檔  
  
1.  開啟資源指令碼檔案。  
  
    > [!NOTE]
    >  如果您的專案尚未包含 .rc 檔，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在 \[[資源檢視](../windows/resource-view-window.md)\] 中，反白顯示資源資料夾 \(例如，MFC.rc\)。  
  
3.  在 [&#91;屬性&#93; 視窗](../Topic/Properties%20Window.md) 中，將 \[**MFC 模式**\] 屬性設為 \[**True**\]。  
  
    > [!NOTE]
    >  除了設定這個旗標外，.rc 檔必須是 MFC 專案的一部分。  比方說，只是在 Win32 專案的 .rc 檔上將 \[**MFC 模式**\] 設為 \[**True**\]，您無法使用任何 MFC 功能。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 MFC  
  
## 請參閱  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)