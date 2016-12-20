---
title: "在框架視窗中拖放檔案 | Microsoft Docs"
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
  - "拖放 [C++], 檔案管理員"
  - "拖放 [C++], 檔案"
  - "拖放 [C++], Windows 檔案總管"
  - "檔案管理員拖放支援"
  - "檔案 [C++], 拖放"
  - "框架視窗 [C++], 在其中拖放檔案"
  - "Windows 檔案總管 [C++]"
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在框架視窗中拖放檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架視窗處理與檔案總管或文件管理員的關聯性。  
  
 將陣列初始化呼叫您的 `CWinApp` 成員函式 `InitInstance`的覆寫如 [CWinApp:應用程式類別。](../mfc/cwinapp-the-application-class.md)中所說明的，因此，您在框架視窗可以間接排列框架視窗開啟檔案被拖曳檔案總管或文件管理員和時發生。  請參閱 [檔案管理員拖放](../mfc/special-cwinapp-services.md)。  
  
## 請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)