---
title: "自訂的安全性影響 | Microsoft Docs"
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
  - "MFC 功能套件, 安全性"
  - "安全性, MFC 功能套件"
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 自訂的安全性影響
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將討論 MFC 潛在的安全性弱點。  
  
## 潛在的安全性漏洞。  
 MFC 提供使用者自訂應用程式使用者介面 \(UI\)，例如，按鈕和圖示外觀的外觀。  MFC 也支援使用者定義的工具，可讓使用者執行 Shell 命令。  因為應用程式的自訂設定在登錄中的使用者設定檔儲存安全性弱點隨即出現。  可以存取登錄的人可以編輯這些設定並變更應用程式的外觀或行為。  例如，電腦的系統管理員可能會造成使用者的應用程式模擬使用者執行任意程式 \(即使是從網路共用\)。  
  
## 替代解決辦法  
 我們建議這三種模式的任一個結束在登錄的缺點:  
  
-   加密儲存自其中的資料  
  
-   將資料儲存在安全的檔案而不是在登錄中。  
  
     若要完成這些前兩種方式之一，從 [CSettingsStore Class](../mfc/reference/csettingsstore-class.md) 衍生類別並覆寫其方法實作加密或儲存在登錄之外。  
  
-   您也可以停用應用程式的自訂。  
  
## 請參閱  
 [MFC 自訂](../mfc/customization-for-mfc.md)