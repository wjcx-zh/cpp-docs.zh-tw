---
title: "在 ActiveX 控制項設定事件處理常式 | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 事件"
  - "事件 [C++], ActiveX 控制項"
ms.assetid: c076386f-c78b-4dc9-9201-a544252d5337
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在 ActiveX 控制項設定事件處理常式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ActiveX 控制項可經由程式設計來回應事件。  您可使用屬性的 **ControlEvents** 來檢視控制項中的可用事件，並建立事件處理常式。  事件處理常用來截取資料來源查詢內的變更。  變更包括：  
  
-   實作查閱。  當某個控制項 \(如 DBCombo 方塊\) 變更值時，該變更事件會被截取，以更新資料控制項的查詢。  
  
-   實作一對多的關聯性。  將兩個資料控制項加入至對話方塊，其中一個是主要部分，另一個則是詳細部分。  每當第一個資料來源變更時，第二個資料來源的查詢就會經由事件處理常式來更新。  
  
-   擷取錯誤。  大多數的控制項都有供您撰寫錯誤處理常式的錯誤事件 \(請參閱[擷取錯誤](../../data/ado-rdo/error-trapping.md)\)。  
  
 如需詳細資訊，請參閱[將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)。  
  
## 請參閱  
 [使用 ActiveX 控制項](../../data/ado-rdo/using-activex-controls.md)