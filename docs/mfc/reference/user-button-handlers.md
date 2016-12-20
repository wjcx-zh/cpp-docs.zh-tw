---
title: "使用者按鈕處理常式 | Microsoft Docs"
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
  - "ON_BN_HILITE"
  - "ON_BN_DOUBLECLICKED"
  - "ON_BN_CLICKED"
  - "ON_BN_PAINT"
  - "ON_BN_DISABLE"
  - "ON_BN_UNHILITE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_BN_CLICKED"
  - "ON_BN_DISABLE"
  - "ON_BN_DOUBLECLICKED"
  - "ON_BN_HILITE"
  - "ON_BN_PAINT"
  - "ON_BN_UNHILITE"
  - "使用者按鈕"
ms.assetid: 410ea968-478f-4806-b7b8-5d7c8dc2bf42
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用者按鈕處理常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列對應項目對應至函式原型。  
  
|對應項目|函式原型|  
|----------|----------|  
|ON\_BN\_CLICKED\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_BN\_DISABLE\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_BN\_DOUBLECLICKED\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_BN\_HILITE\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_BN\_PAINT\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
|ON\_BN\_UNHILITE\( \<id\>, \<memberFxn\> \)|afx\_msg void memberFxn \(\);|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)