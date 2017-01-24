---
title: "MFC ActiveX 控制項：建立 Automation 伺服程式 | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], Automation 伺服程式"
  - "Automation 伺服程式 [C++], MFC ActiveX 控制項"
  - "MFC ActiveX 控制項 [C++], Automation 伺服程式"
ms.assetid: e0c24ed2-d61c-49ad-a4fa-4e1098d1d39b
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：建立 Automation 伺服程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以開發 MFC ActiveX 控制項做為 Automation 伺服程式提供以程式設計的方式將該控制項在其他應用程式和呼叫方法的目的是在應用程式中的控制項。  這類控制項可以裝載 ActiveX 控制項容器。  
  
### 建立控制項做為 Automation 伺服程式  
  
1.  [建立](../mfc/reference/mfc-activex-control-wizard.md) 控制項。  
  
2.  [Add 方法](../mfc/mfc-activex-controls-methods.md)。  
  
3.  覆寫 [IsInvokeAllowed](../Topic/COleControl::IsInvokeAllowed.md)。  如需詳細資訊，請參閱知識庫文件 Q146120。  
  
4.  建置控制項。  
  
### 以程式設計方式存取在 Automation 伺服程式的方法  
  
1.  建立應用程式，例如， [MFC exe](../mfc/reference/mfc-application-wizard.md)。  
  
2.  在 `InitInstance` 函式的開頭，加入下列程式碼:  
  
     [!code-cpp[NVC_MFC_AxCont#17](../mfc/codesnippet/CPP/mfc-activex-controls-creating-an-automation-server_1.cpp)]  
  
3.  在類別檢視中，以滑鼠右鍵按一下專案節點並選取 **Add class from typelib** 匯入型別程式庫。  
  
     這會將副檔名為 .h 和 .cpp 檔案加入至專案。  
  
4.  在您將會在 ActiveX 控制項的一或多個方法類別的標頭檔，請將下列程式碼: `#include filename.h`，其中的檔名是建立標頭檔的名稱，當您匯入型別程式庫。  
  
5.  在呼叫將會對在 ActiveX 控制項的方法的函式，建立控制項的包裝函式類別的物件中加入、修改和 ActiveX 物件。  例如，在中，當 OK 按鈕顯示在對話方塊中，按一下下列 MFC 程式碼具現化 `CCirc` 控制項，取得標頭屬性，並顯示結果:  
  
     [!code-cpp[NVC_MFC_AxCont#18](../mfc/codesnippet/CPP/mfc-activex-controls-creating-an-automation-server_2.cpp)]  
  
 如果您將方法加入至 ActiveX 控制項，在應用程式之後使用它，您可以開始使用控制項的最新版本應用程式藉由刪除建置的檔案，在匯入型別程式庫。  然後再次匯入型別程式庫。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)