---
title: "CWinApp 和 MFC 應用程式精靈 | Microsoft Docs"
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
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式精靈 [C++], 和 CWinApp"
  - "CWinApp 類別, 和 MFC 應用程式精靈"
  - "MFC [C++], 精靈"
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinApp 和 MFC 應用程式精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在建立基本架構應用程式時， MFC 應用程式精靈宣告應用程式類別會衍生自 [CWinApp](../mfc/reference/cwinapp-class.md)。  MFC 應用程式精靈也會包含下列項目的實作檔:  
  
-   應用程式類別的訊息對應。  
  
-   空的類別建構函式。  
  
-   宣告類別的只有物件的變數。  
  
-   您的 `InitInstance` 成員函式的標準實作。  
  
 應用程式類別以專案標題和主要原始程式檔位置。  建立的類別和檔案的名稱是根據您在 MFC 應用程式精靈提供的專案名稱。  最簡單的方式來檢視這些類別的程式碼是透過 [類別檢視](http://msdn.microsoft.com/zh-tw/8d7430a9-3e33-454c-a9e1-a85e3d2db925)。  
  
 提供的標準實作和訊息對應用於許多用途是完整的，不過，您可以修改它們需要。  最這些實作是 `InitInstance` 成員函式。  通常，您會將程式碼加入至 `InitInstance`的基本架構實作。  
  
## 請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)   
 [可覆寫的 CWinApp 成員函式](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊 CWinApp 服務](../mfc/special-cwinapp-services.md)