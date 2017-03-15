---
title: "ATL COM 屬性頁 | Microsoft Docs"
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
  - "ATL COM 物件"
  - "ATL 屬性頁"
  - "COM 物件, ATL"
  - "COM 屬性頁"
  - "屬性頁, ATL"
  - "屬性頁, COM"
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ATL COM 屬性頁
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM 屬性頁來設定屬性 \(或呼叫方法\) 提供使用者介面 \(UI\) 的一或多個 COM 物件。  ActiveX 控制項常用屬性頁提供允許控制項屬性在設計階段豐富的使用者介面。  
  
 屬性頁是實作 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) 或 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) 介面的 COM 物件。  這些介面提供允許頁面與 `site` 的方法 \(表示頁面的容器\) 的 COM 物件和一些 *物件* \(方法會呼叫以回應屬性頁使用者所做的變更\) 的 COM 物件。  屬性頁容器何時何時會呼叫在屬性頁中介面的方法負責呼叫頁面會顯示或隱藏其使用者介面和應用程式使用者所做的變更至基礎物件。  
  
 每個屬性頁可以獨立屬性上設定的物件完全被建置。  屬性頁需要的是了解特定介面 \(或一組介面\) 以及呼叫方法提供使用者介面用於該介面。  
  
 如需詳細資訊，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [屬性工作表的屬性頁](http://msdn.microsoft.com/library/windows/desktop/ms686577) 。  
  
## 本章節內容  
 [指定屬性頁](../atl/specifying-property-pages.md)  
 清單中指定的屬性頁中您的控制項並顯示範例類別。  
  
 [實作屬性頁](../atl/implementing-property-pages.md)  
 列出實作的屬性頁中，包括方法覆寫。  逐步引導您根據 ATLPages 範例程式的完整範例。  
  
## 相關章節  
 [ATLPages 範例](../top/visual-cpp-samples.md)  
 ATLPages 範例的範例摘要，使用 `IPropertyPageImpl`，實作屬性頁。  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 使用 Active Template Library，提供概念性主題連結說明如何撰寫程式。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)