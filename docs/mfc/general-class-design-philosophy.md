---
title: "一般類別設計原理 | Microsoft Docs"
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
  - "vc.classes.mfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "類別 [C++], MFC 類別設計"
  - "設計類別"
  - "MFC [C++], Windows 應用程式開發介面"
  - "Visual C, Windows 應用程式開發介面呼叫"
  - "Windows API [C++], 與 MFC"
ms.assetid: e6861ae0-1581-4d9c-9ddf-63f9afcdb913
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般類別設計原理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 C\+\+ 語言變得普遍之前， Microsoft Windows 所設計的。  由於數千應用程式使用 C 語言 Windows 應用程式 Interface \(API\)，該介面會維持在可預見的未來。  必須建立讓所有 C\+\+ Windows 介面在 C 程式設計語言 API 之上。  這可確保 C\+\+ 應用程式中同時使用 C\# 應用程式。  
  
 MFC 程式庫是達成下列設計目標的物件導向介面到視窗:  
  
-   對工作大幅降低撰寫的 Windows 應用程式。  
  
-   執行速度比較與 C 語言應用程式開發介面。  
  
-   最小程式碼大小的額外負荷。  
  
-   能夠直接呼叫任何視窗 C 函式。  
  
-   現有的 C\# 應用程式更容易轉換成 C\+\+。  
  
-   可從 C 語言視窗現有基底設計經驗的支援。  
  
-   對運用 C\+\+ 的 Windows API 的比較容易使用與 C。  
  
-   更容易使用，複雜的功能強大的抽象 \(如 ActiveX 控制項、資料庫支援、列印、工具列和狀態列。  
  
-   true 表示有效地使用 C\+\+ 語言功能的 C\+\+ 的 Windows 應用程式開發介面。  
  
 如需在 MFC 程式庫的設計，請參閱:  
  
-   [應用程式架構](../mfc/application-framework.md)  
  
-   [對 C 語言 API 的關聯性](../mfc/relationship-to-the-c-language-api.md)  
  
## 請參閱  
 [類別概觀](../mfc/class-library-overview.md)