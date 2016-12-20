---
title: "將表單插入專案中 | Microsoft Docs"
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
  - "表單, 加入至專案"
  - "插入新項目對話方塊"
  - "插入表單"
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將表單插入專案中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表單為控制項提供便利的容器。  只要應用程式支援 MFC 程式庫，您可以輕鬆地插入一個 MFC 架構的表單至應用程式。  
  
### 將表單加入至專案  
  
1.  從類別檢視中，選取您要加入表單的專案，然後按一下滑鼠右鍵。  
  
2.  在捷徑功能表中，按一下 \[加入\] 後再按一下 \[加入類別\]。  
  
     如果 **New Form** 命令無法使用，您的專案可能會因 Active Template Library \(ATL\)。  首次建立專案，將表單加入至 ATL 專案，您必須 [指定某些設定](../atl/reference/application-settings-atl-project-wizard.md) 。  
  
3.  從 **MFC** 資料夾，按一下 **MFC Class**。  
  
4.  使用 MFC 類別精靈，請建立新的類別會衍生自 [CFormView](../mfc/reference/cformview-class.md)。  
  
 Visual C\+\+ 將表單加入至您的應用程式，開啟它在對話方塊編輯器內，以便開始加入控制項和工作在它的整體設計。  
  
 您可以執行下列額外步驟 \(不適用於對話方塊架構應用程式\):  
  
1.  覆寫 `OnUpdate` 成員函式。  
  
2.  實作 10% 成員函式從您要將資料移到您的文件。  
  
3.  建立 `OnPrint` 成員函式。  
  
## 請參閱  
 [表單檢視](../mfc/form-views-mfc.md)