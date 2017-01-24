---
title: "ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數 | Microsoft Docs"
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
  - "ActiveX 控制項容器 [C++], 存取 ActiveX 控制項"
  - "ActiveX 控制項容器 [C++], ActiveX 控制項做為成員變數"
  - "ActiveX 控制項 [C++], 存取"
  - "ActiveX 控制項 [C++], 專案的成員變數"
  - "將 ActiveX 控制項連接到容器成員變數"
  - "成員變數 [C++], 專案中的 ActiveX 控制項"
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控制項容器：將 ActiveX 控制項連接至成員變數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

存取 ActiveX 控制項與其控制項容器應用程式中與關聯 ActiveX 控制項與將包含控制項的對話方塊類別的成員變數。  
  
> [!NOTE]
>  這不是唯一可以存取內嵌控制項從容器類別的內部，不過，為本文即可。  
  
### 將成員變數加入至對話方塊類別。  
  
1.  從類別檢視中，以滑鼠右鍵按一下主對話方塊類別開啟捷徑功能表。  例如 `CContainerDlg`。  
  
2.  從捷徑功能表上按一下**加入**，然後按一下 \[**加入變數**\]。  
  
3.  在加入成員變數精靈中，按一下 **Control variable**。  
  
4.  在 **Control ID** 清單方塊中，選取內嵌 ActiveX 控制項的控制項 ID。  例如 `IDC_CIRCCTRL1`。  
  
5.  在**變數名稱** 方塊中，輸入名稱。  
  
     例如 `m_circctl`。  
  
6.  按一下 **Finish** 接受您的索引和結尾加入成員變數精靈。  
  
## 請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)