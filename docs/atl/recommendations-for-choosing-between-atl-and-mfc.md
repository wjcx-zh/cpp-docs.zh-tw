---
title: "Recommendations for Choosing Between ATL and MFC | Microsoft Docs"
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
  - "ATL, 和 MFC 的比較"
  - "MFC, ATL 支援"
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Recommendations for Choosing Between ATL and MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在開發元件和應用程式時，您可以選擇在這兩種方法之間的 ATL 和 MFC \(MFC 程式庫\)。  
  
## 使用 ATL  
 ATL 是一個快速而輕鬆的方法，以建立在 C\+\+ 中使用 COM 元件並維護較小耗用量。  請使用 ATL 建置控制項，如果不需要 MFC 自動提供的所有內建的功能。  
  
## 使用 MFC  
 MFC 可讓您建立完成的應用程式、ActiveX 控制項和主動式文件。  如果您已經建立 MFC 的控制項，您可以繼續在 MFC 的開發。  當建立新的控制項時，請考慮使用 ATL，如果不需要任何 MFC 的內建功能。  
  
## 使用 MFC 中的 ATL 專案  
 您可以執行精靈加入 ATL 支援使用現有的 MFC 專案。  如需詳細資訊，請參閱 [將 ATL 支援加入至 MFC 專案](../mfc/reference/adding-atl-support-to-your-mfc-project.md)。  
  
## 請參閱  
 [ATL 簡介](../atl/introduction-to-atl.md)