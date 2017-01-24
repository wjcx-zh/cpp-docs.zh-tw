---
title: "下拉式方塊處理常式 | Microsoft Docs"
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
  - "ON_CBN_KILLFOCUS"
  - "ON_CBN_ERRSPACE"
  - "ON_CBN_EDITCHANGE"
  - "ON_CBN_CLOSEUP"
  - "ON_CBN_DBLCLK"
  - "ON_CBN_EDITUPDATE"
  - "ON_CBN_DROPDOWN"
  - "ON_CBN_SELENDOK"
  - "ON_CBN_SELCHANGE"
  - "ON_CBN_SETFOCUS"
  - "ON_CBN_SELENDCANCEL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "下拉式方塊, 處理常式"
  - "ON_CBN_CLOSEUP"
  - "ON_CBN_DBLCLK"
  - "ON_CBN_DROPDOWN"
  - "ON_CBN_EDITCHANGE"
  - "ON_CBN_EDITUPDATE"
  - "ON_CBN_ERRSPACE"
  - "ON_CBN_KILLFOCUS"
  - "ON_CBN_SELCHANGE"
  - "ON_CBN_SELENDCANCEL"
  - "ON_CBN_SELENDOK"
  - "ON_CBN_SETFOCUS"
ms.assetid: 7f092412-01b7-4242-95ec-41ba506b9d71
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 下拉式方塊處理常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列對應項目對應至函式原型。  
  
|對應項目|函式原型|  
|----------|----------|  
|ON\_CBN\_CLOSEUP \( \<ID\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\)|  
|ON\_CBN\_DBLCLK \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_DROPDOWN \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_EDITCHANGE \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_EDITUPDATE \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_ERRSPACE \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_KILLFOCUS \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_SELCHANGE \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_SELENDCANCEL \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_SELENDOK \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_CBN\_SETFOCUS \( \<id\>， \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)