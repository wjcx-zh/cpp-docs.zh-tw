---
title: "Active Template Library (ATL) 概念 | Microsoft Docs"
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
  - "ATL, 關於 ATL"
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
caps.latest.revision: 18
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Active Template Library (ATL) 概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Active Template Library \(ATL\) 是一種可讓您建立小型，快速的元件物件模型 \(COM\) \(COM\) 物件的一組樣板架構的 C\+\+ 類別。  它具有特殊支援主要 COM 功能，包括內建 \(Stock\) 實作，雙重介面，標準 COM 列舉值介面，連接點， Tear\-Off 介面和 ActiveX 控制項。  
  
 如果您進行大量的 ATL，您會想要進一步了解屬性，其設計是要簡化 COM 程式設計在 Visual C\+\+ .NET 的新功能。  如需詳細資訊，請參閱 [屬性化程式設計](../windows/attributed-programming-concepts.md)。  
  
## 在本節中  
 [ATL 教學課程](../atl/active-template-library-atl-tutorial.md)  
 引導您建立控制項，並在處理時示範一些 ATL 基本概念。  
  
 [COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)  
 引進了元件物件模型 \(COM\) \(COM\) 背後的主要概念。  本文將簡短也說明什麼是 ATL，而且，則您應該使用它。  
  
 [ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)  
 討論各種 ATL 類別之間的關聯，而且這些類別如何實作。  
  
 [雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)  
 描述 ATL 雙重介面方面。  
  
 [ATL 集合和列舉值。](../atl/atl-collections-and-enumerators.md)  
 說明 ATL 集合和列舉值的實作和建立。  
  
 [複合控制項的基本概念](../atl/atl-composite-control-fundamentals.md)  
 提供建立複合控制項的逐步指示。  複合控制項是可以包含其他 ActiveX 控制項或視窗控制 ActiveX 控制項的型別。  
  
 [ATL 控制項內含項目 FAQ](../atl/atl-control-containment-faq.md)  
 使用 ATL 涵蓋基礎問題與裝載控制項。  
  
 [ATL COM 屬性頁](../atl/atl-com-property-pages.md)  
 示範如何指定並實作 COM 屬性頁。  
  
 [ATL 支援 DHTML 控制項](../atl/atl-support-for-dhtml-controls.md)  
 提供建立 DHTML 控制項的逐步指示。  
  
 [ATL 連接點](../atl/atl-connection-points.md)  
 說明何謂連接點是，而 ATL 如何實作它們。  
  
 [事件處理常式和 ATL](../atl/event-handling-and-atl.md)  
 描述如何使用 ATL 的 [IDispEventImpl](../atl/reference/idispeventimpl-class.md) 和 [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) 類別，您必須採取以處理 COM 事件的步驟。  
  
 [ATL 及無限制執行緒封送處理器](../atl/atl-and-the-free-threaded-marshaler.md)  
 可讓您的類別彙總 \(Aggregate\) 無限制執行緒封送處理器 \(FTM\) 的 ATL 簡單物件精靈中選取  選項的詳細資料。  
  
 [指定專案的執行緒模型](../atl/specifying-the-threading-model-for-a-project-atl.md)  
 說明可用控制項的執行階段效能相關至執行緒在專案的巨集。  
  
 [ATL 模組類別](../atl/atl-module-classes.md)  
 討論模組類別新的 ATL 7.0。  模組的基本功能由 ATL 需要實作的類別。  
  
 [ATL 服務](../atl/atl-services.md)  
 報告時所發生的一系列事件，當服務中實作時。  同時也會討論一些概念與開發服務相關。  
  
 [ATL 視窗類別](../atl/atl-window-classes.md)  
 說明如何建立，超級類別和子類別視窗在 ATL。  ATL 視窗類別不是 COM 類別。  
  
 [ATL 集合類別](../atl/atl-collection-classes.md)  
 說明 ATL 如何使用陣列和對應。  
  
 [ATL 註冊元件 \(系統管理員\)](../atl/atl-registry-component-registrar.md)  
 討論指令碼語法和可取代參數的 ATL。  它也說明如何設定靜態連結顯示給管理員。  
  
 [利用 ATL 和 C 執行階段程式碼](../atl/programming-with-atl-and-c-run-time-code.md)  
 討論靜態或動態連結的優點至 C 執行階段程式庫 \(CRT\)。  
  
 [利用 CComBSTR](../atl/programming-with-ccombstr-atl.md)  
 討論需求時，會利用 `CComBSTR`時的數種情況。  
  
 [編碼方式參考](../atl/atl-encoding-reference.md)  
 提供支援在一般網際網路標準範圍的編碼方式 \(例如 uuencode、十六進位和 UTF8 atlenc.h 中的函式和巨集。  
  
 [公用程式參考](../atl/atl-utilities-reference.md)  
 以 [CPathT](../atl/reference/cpatht-class.md) 和 [卷毛](../atl/reference/curl-class.md)的形式，提供管理的路徑和 URL 的程式碼。  執行緒集區， [CThreadPool](../atl/reference/cthreadpool-class.md)，可用於應用程式。  這個程式碼可以在類別和函式找到。  
  
## 相關章節  
 [ATL 範例](../top/visual-cpp-samples.md)  
 提供描述並連結至 ATL 範例程式。  
  
 [建立 ATL 專案](../atl/reference/creating-an-atl-project.md)  
 包含關於 ATL 專案精靈的資訊。  
  
 [ATL 控制項精靈](../atl/reference/atl-control-wizard.md)  
 討論如何將類別。  
  
 [屬性化程式設計](../windows/attributed-programming-concepts.md)  
 提供有關使用概觀屬性簡化加上連結清單的 COM 更詳細的主題。  
  
 [ATL 類別概觀](../atl/atl-class-overview.md)  
 提供參考資訊，而 ATL 的連結分類。