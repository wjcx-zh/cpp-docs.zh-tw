---
title: "ActiveX 控制項容器 | Microsoft Docs"
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
  - "ActiveX 控制項容器 [C++]"
  - "OLE 控制項 [C++], 容器"
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控制項容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項容器是完全支援 ActiveX 控制項，而且可以合併至其視窗或對話方塊中的容器。  ActiveX 控制項是您在許多開發專案可以使用的可重複使用的軟體項目。  控制項可讓您的應用程式的使用者存取資料庫，監視資料，並在您的應用程式中的各種選項。  如需 ActiveX 控制項的詳細資訊，請參閱[MFC 控制項](../mfc/mfc-activex-controls.md)文件。  
  
 容器控制項通常會在專案的兩個表單：  
  
-   對話方塊和像對話方塊的視窗 ，例如表單檢視， ActiveX 控制項在對話方塊中使用某個位置。  
  
-   視窗在應用程式中， ActiveX 控制項用於工具列，或其他位置使用者視窗的。  
  
 ActiveX 控制項容器與控制項互動透過公開的 [方法](../mfc/mfc-activex-controls-methods.md) 和 [屬性](../mfc/mfc-activex-controls-properties.md)。  這些方法和屬性，可以控制容器存取和修改，您可以在 ActiveX 控制項容器專案的包裝函式類別存取。  內嵌 ActiveX 控制項可能與容器互動所引發的 \(傳送\) [事件](../mfc/mfc-activex-controls-events.md) 告知容器發生的次數。  控制項容器可以選取動作在這些通知。  
  
 其他文件討論幾個主題，從建立 ActiveX 控制項容器專案對基底實作問題與建置的 ActiveX 控制項容器相關與 Visual C\+\+:  
  
-   [建立 MFC ActiveX 控制項容器](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [ActiveX 控制項的容器](../mfc/containers-for-activex-controls.md)  
  
-   [ActiveX 控制項容器：手動啟用 ActiveX 控制項內含項目](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [ActiveX 控制項容器：將控制項插入控制項容器應用程式中](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [ActiveX 控制項容器：從 ActiveX 控制項中處理事件](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [ActiveX 控制項容器：檢視和修改控制項屬性](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [ActiveX 控制項容器：在非對話方塊容器中使用控制項](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 如需使用 ActiveX 控制項的詳細資訊的對話方塊，請參閱 [對話方塊編輯器](../mfc/dialog-editor.md) 主題。  
  
 使用 Visual C\+\+ 和 MFC ActiveX 控制項類別，如需說明開發 ActiveX 控制項詳細資料文件的清單，請參閱 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)。  文件的功能類別群組。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)