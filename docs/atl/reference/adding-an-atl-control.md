---
title: "加入 ATL 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 加入控制項"
  - "控制項 [ATL], 加入至專案"
ms.assetid: 10223e7e-fdb7-4163-80c6-44aeafa8e6ce
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入 ATL 控制項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用這個精靈來將使用者介面物件加入至支援所有可能容器 \(Container\) 介面的專案。  若要支援這些介面，專案必須是建立為 ATL 應用程式或包含 ATL 支援的 MFC 應用程式。  您可以使用 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)來建立 ATL 應用程式，或[將 ATL 支援加入至 MFC 專案](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)來為 MFC 應用程式實作 ATL 支援。  
  
### 若要將 ATL 控制項加入至您的專案  
  
1.  在 \[**方案總管**\] 或[類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，以滑鼠右鍵按一下您要加入 ATL 簡單物件的專案名稱。  
  
2.  按一下捷徑功能表中的 \[**加入**\]，然後按一下 \[**加入類別**\]。  
  
3.  在[加入類別](../../ide/add-class-dialog-box.md)對話方塊的範本窗格中，按一下 \[**ATL 控制項**\]，然後按一下 \[**加入**\] 以顯示 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)。  
  
 使用 \[**ATL 控制項精靈**\]，您可建立以下任一類型的控制項：  
  
-   標準控制項  
  
-   複合控制項  
  
-   DHTML 控制項  
  
 除此之外，您可以選取精靈 \[**選項**\] 頁面上的 \[**最小控制項**\] 來減少控制項的大小並移除多數容器不使用的介面。  
  
## 請參閱  
 [Adding Functionality to the Composite Control](../../atl/adding-functionality-to-the-composite-control.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [ATLFire Sample](http://msdn.microsoft.com/zh-tw/5b2649f1-f45b-4cfb-9c4b-4d9459c26b09)