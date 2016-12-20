---
title: "將物件和控制項加入至 ATL 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控制項精靈"
  - "ATL 專案, 加入控制項"
  - "ATL 專案, 加入物件"
  - "控制項 [ATL], 加入至專案"
  - "物件 [C++], 加入至 ATL 專案"
  - "精靈 [C++], ATL 專案"
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將物件和控制項加入至 ATL 專案
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用任一 ATL 程式碼精靈來將物件或控制項加入至 ATL 或 MFC 架構專案。  針對您加入的每個 COM 物件或控制項，精靈會產生 .cpp、.h 檔以及指令碼架構登錄支援的 .rgs 檔。  Visual Studio 中有下列 ATL 程式碼精靈可使用：  
  
||||  
|-|-|-|  
|[ATL 簡單物件](../../atl/reference/atl-simple-object-wizard.md)|[ATL 對話方塊](../../atl/reference/atl-dialog-wizard.md)|[ATL 控制項](../../atl/reference/atl-control-wizard.md)|  
|[ATL 屬性頁](../../atl/reference/atl-property-page-wizard.md)|[ATL Active Server Page 元件](../../atl/reference/atl-active-server-page-component-wizard.md)|[ATL OLE DB 消費者](../../atl/reference/atl-ole-db-consumer-wizard.md)|  
|[將 ATL 支援加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[ATL COM\+ 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[ATL OLE DB 提供者](../../atl/reference/atl-ole-db-provider-wizard.md)|  
  
> [!NOTE]
>  在將 ATL 物件加入至專案之前，您應檢視物件相關說明主題中的詳細資訊和需求。  
  
### 若要使用 ATL 控制項精靈加入物件或控制項  
  
1.  在 \[方案總管\] 中以滑鼠右鍵按一下專案節點，然後在捷徑功能表上按一下 \[加入\]。  按一下 \[加入類別\]。  
  
     [加入類別](../../ide/add-class-dialog-box.md)對話方塊隨即出現。  
  
2.  選取 \[類別\] 窗格的 \[ATL\] 資料夾，接著從 \[範本\] 窗格選取要插入的物件。  按一下 \[**開啟**\]。  接著會出現選取物件的程式碼精靈。  
  
    > [!NOTE]
    >  如果要將 ATL 物件加入至 MFC 專案，您必須將 ATL 支援加入至現有專案。  您可以依照[將 ATL 支援加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)中的指示來這麼做。  
  
     此外，如果嘗試將 ATL 物件加入至 MFC 專案，而之前並未加入 ATL 支援的話，Visual Studio 會提示您是否要將 ATL 支援加入至專案。  按一下 \[**是**\] 將 ATL 支援加入至專案並開啟選取的 ATL 精靈。  
  
## 請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)