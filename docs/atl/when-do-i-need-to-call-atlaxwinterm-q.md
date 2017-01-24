---
title: "When Do I Need to Call AtlAxWinTerm? | Microsoft Docs"
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
  - "AtlAxWinTerm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlAxWinTerm method"
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: 12
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# When Do I Need to Call AtlAxWinTerm?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[AtlAxWinTerm](../Topic/AtlAxWinTerm.md) **"AtlAxWin80"** 取消註冊視窗類別。  您應該呼叫這個函式 \(如果您不再需要建立裝載視窗\)，在終結之後所有現有的主視窗。  如果您未呼叫這個函式，視窗類別會自動移除註冊時，在處理序終止。  
  
## 請參閱  
 [When Do I Need to Call AtlAxWinInit?](../atl/when-do-i-need-to-call-atlaxwininit-q.md)   
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)