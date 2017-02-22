---
title: "ActiveX 控制項容器：檢視和修改控制項屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項容器 [C++], 檢視及修改屬性"
  - "ActiveX 控制項 [C++], 屬性"
  - "控制項 [MFC], 屬性"
  - "屬性 [MFC], 檢視及修改"
  - "資源編輯器, 檢視及修改 ActiveX 控制項"
ms.assetid: 14ce5152-742b-4e0d-a9ab-c7b456e32918
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ActiveX 控制項容器：檢視和修改控制項屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您將 ActiveX 控制項編譯專案時，檢視和變更 ActiveX 控制項支援的屬性非常有用。  本文將討論如何使用 Visual C\+\+ 資源編輯器來做。  
  
 如果 ActiveX 控制項容器應用程式使用內嵌控制項，您可以檢視和修改控制項的屬性，在資源編輯器中。  在設計階段，您也可以使用資源編輯器設定屬性值。  資源編輯器自動更新儲存在專案的資源檔中的這些值。  控制項的所有執行個體並將其屬性初始化為這些值。  
  
 這個程序假設您插入控制項至您的專案中。  如需詳細資訊，請參閱 [ActiveX 控制項容器:插入至控制項容器應用程式](../mfc/inserting-a-control-into-a-control-container-application.md)。  
  
 第一步檢視中控制項的屬性將加入控制項的執行個體加入至專案的對話方塊範本。  
  
### 若要檢視使用者控制項的屬性  
  
1.  在資源檢視中，開啟 **Dialog** 資料夾。  
  
2.  開啟您的主對話方塊範本。  
  
3.  使用 \[**插入 ActiveX 控制項**\] 對話方塊，將 ActiveX 控制項。  如需詳細資訊，請參閱 [檢視及加入 ActiveX 控制項加入至對話方塊](../mfc/viewing-and-adding-activex-controls-to-a-dialog-box.md)。  
  
4.  在對話方塊中，選取 ActiveX 控制項。  
  
5.  從 \[屬性\] 視窗中，按一下 \[**屬性**\] 按鈕。  
  
 使用 \[**屬性**\] 對話方塊會立即修改和測試新的屬性。  
  
## 請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)