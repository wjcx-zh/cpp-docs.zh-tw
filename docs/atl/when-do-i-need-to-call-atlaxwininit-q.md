---
title: "When Do I Need to Call AtlAxWinInit? | Microsoft Docs"
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
  - "AtlAxWinInit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlAxWinInit method"
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# When Do I Need to Call AtlAxWinInit?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[AtlAxWinInit](../Topic/AtlAxWinInit.md) 註冊 **"AtlAxWin80"** 視窗類別 \(加上兩個自訂 Windows 訊息\)，因此必須呼叫這個函式，在您嘗試建立裝載視窗之前。  不過，您永遠都不需要明確地呼叫這個函式，，因為使用這些類別\) 的裝載 API \(以及類別通常您呼叫此函式。  沒有在多次呼叫這個函式的損害。  如需詳細資訊，請參閱 [什麼是 ATL 控制項裝載 API?](../atl/what-is-the-atl-control-hosting-api-q.md)。  
  
## 請參閱  
 [When Do I Need to Call AtlAxWinTerm?](../atl/when-do-i-need-to-call-atlaxwinterm-q.md)   
 [控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)