---
title: "檢查精靈的結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "自訂精靈, 精靈專案"
ms.assetid: 79917075-a843-40f6-abf8-64d98e5f6bdc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 檢查精靈的結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您不需要編譯精靈專案，使用者也可立即使用。  一旦您建立了必要項目之後，VSDIR 即指示 \[`New Project`\] 對話方塊顯示精靈圖示，並指示 \[`Add New Item`\] 對話方塊在捷徑功能表中顯示該精靈名稱。  您的客戶只要選取精靈即可立即啟動精靈。  
  
 當使用者啟動精靈時，環境 Shell 會共同建立精靈引擎並查詢 <xref:EnvDTE.IDTWizard>。  然後它會呼叫 <xref:EnvDTE.IDTWizard.Execute%2A> 來啟動精靈。  
  
> [!NOTE]
>  如果精靈沒有介面，就會以提供的預設值建立專案，並顯示於 \[方案總管\] 中，其具有 .vsz 檔案所提供的節點結構。  本主題的其餘內容皆假設精靈具有 UI 來說明。  
  
 如果精靈具有 UI，則使用者會在精靈的 HTML 架構 UI 的每個控制項中接受或變更預設設定。  當使用者瀏覽精靈的頁面並進行變更的同時，HTML 的 Script 區段中會呼叫諸如 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.Navigate%2A> 和 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.Next%2A> 等函式。  
  
 每當使用者選取精靈內的不同選項時，精靈控制項的符號表便會擷取這些選取。  此符號表會比對精靈 HTML 網頁中的控制項 ID，來維護使用者選取與符號表之間的一對一對應。  
  
 當使用者在精靈 UI 按一下 \[**完成**\] 時，HTML 指令碼便會呼叫 JScript 函式 **OnFinish**。  
  
> [!NOTE]
>  您可自訂 Default.js 中的 **OnFinish** 來執行您需要的任何其他工作。  
  
 精靈引擎接著會搜尋樣板檔案，根據使用者的選擇進行剖析和轉譯。  它會將轉譯的檔案複製到專案目錄，並將這些檔案加入至專案。  新建的專案會載入 Visual Studio 環境中，而專案節點和檔案會顯示在 \[方案總管\] 中。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl>   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈步驟](../ide/steps-to-designing-a-wizard.md)   
 [自訂精靈](../ide/customizing-your-wizard.md)