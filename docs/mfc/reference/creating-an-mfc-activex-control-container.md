---
title: "建立 MFC ActiveX 控制項容器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.activex.container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項容器 [C++], 建立"
  - "容器 [C++], 建立"
  - "MFC ActiveX 控制項 [C++], 容器"
  - "OLE 控制項 [C++], 容器"
ms.assetid: ec70e137-7c14-4940-bd0e-fd4edcc63ea5
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立 MFC ActiveX 控制項容器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項容器 \(Container\) 是一個為 ActiveX \(先前的 OLE\) 控制項提供執行環境的父程式。  不論使用或不使用 MFC，您都能建立一個可包含 ActiveX 控制項的應用程式，但是使用 MFC 較容易辦到。  
  
 使用 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)建立一個 MFC 容器程式，使您可以存取由 MFC 和 ActiveX 類別實作的許多 ActiveX 控制項和 Automation 之功能。  這些功能包括視覺化編輯、Automation、建立複合檔案和控制項支援。  您的父程式所支援的 MFC 應用程式精靈視覺化編輯選項包括建立一個容器、一個迷你伺服程式 \(Mini\-Server\)、一個全伺服程式 \(Full\-Server\) 和一個既是容器也是伺服程式的程式。  
  
-   **新增 MFC 應用程式**。  若要建立一個包含 Automation、視覺化編輯、複合檔案或控制項支援的新 MFC 程式，請使用 MFC 應用程式精靈並選擇適當的 Automation 選項。  
  
-   **現有的 MFC 應用程式**。  若您要將控制項內含項目加入至現有的 MFC 應用程式，請參閱 [OLE 控制項容器：手動啟用 OLE 控制項內含項目](../../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)。  
  
### 若要為以下任一類型的應用程式建立 ActiveX 容器  
  
1.  [容器](../../mfc/containers.md)  
  
2.  [視覺化編輯](../../mfc/ole-mfc.md)  
  
3.  [MFC ActiveX 控制項](../../mfc/mfc-activex-controls.md)  
  
## 請參閱  
 [Visual C\+\+ 專案類型](../../ide/visual-cpp-project-types.md)