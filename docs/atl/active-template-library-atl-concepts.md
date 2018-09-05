---
title: Active Template Library (ATL) 概念 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bb07807934dcc5c665f0058ef869f62f0b2d3ea
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755420"
---
# <a name="active-template-library-atl-concepts"></a>Active Template Library (ATL) 概念

Active Template Library (ATL) 是一份樣板架構 c + + 類別，可讓您建立小型、 快速的元件物件模型 (COM) 物件。 它有索引鍵的 COM 功能，包括內建實作、 雙重介面、 標準的 COM 列舉程式介面、 連接點、 tear-off 介面和 ActiveX 控制項的特殊支援。

如果您這麼做了很多 ATL 程式，您會想要深入了解屬性，旨在簡化 COM 程式開發的 Visual c + +.NET 中的新功能。 如需詳細資訊，請參閱 <<c0> [ 屬性化程式設計](../windows/attributed-programming-concepts.md)。

## <a name="in-this-section"></a>本節內容

[ATL 教學課程](../atl/active-template-library-atl-tutorial.md)  
將引導您完成建立控制項，並示範一些程序中的 ATL 基本概念。

[COM 和 ATL 簡介](../atl/introduction-to-com-and-atl.md)  
引進了元件物件模型 (COM) 背後的主要概念。 這篇文章也簡短說明 ATL 為何和何時應該使用它。

[ATL COM 物件的基本概念](../atl/fundamentals-of-atl-com-objects.md)  
討論各種 ATL 類別，以及這些類別的實作方式之間的關聯性。

[雙重介面和 ATL](../atl/dual-interfaces-and-atl.md)  
說明 ATL 觀點的雙重介面。

[ATL 集合和列舉程式](../atl/atl-collections-and-enumerators.md)  
描述的集合和 ATL 中的列舉程式的建立與實作

[複合控制項基本概念](../atl/atl-composite-control-fundamentals.md)  
提供用來建立複合控制項的逐步指示。 複合控制項是一種可包含其他 ActiveX 控制項或 Windows 控制項的 ActiveX 控制項。

[ATL 控制項內含項目常見問題集](../atl/atl-control-containment-faq.md)  
涵蓋基本與主機使用 ATL 的控制項相關的問題

[ATL COM 屬性頁](../atl/atl-com-property-pages.md)  
說明如何指定及實作 COM 屬性頁。

[DHTML 控制項的 ATL 支援](../atl/atl-support-for-dhtml-controls.md)  
提供用來建立 DHTML 控制項的逐步指示。

[ATL 連接點](../atl/atl-connection-points.md)  
說明連接點是什麼，以及 ATL 如何實作它們。

[事件處理和 ATL](../atl/event-handling-and-atl.md)  
說明您需要採取來處理使用 ATL 的 COM 事件的步驟[IDispEventImpl](../atl/reference/idispeventimpl-class.md)並[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)類別。

[ATL 和無限制執行緒封送處理器](../atl/atl-and-the-free-threaded-marshaler.md)  
[ATL 簡單物件精靈] 的選項，可讓您的類別來彙總無限制執行緒封送處理器 (FTM) 提供詳細資料。

[指定專案的執行緒模型](../atl/specifying-the-threading-model-for-a-project-atl.md)  
描述可用來控制執行階段效能與您的專案中的執行緒相關的巨集。

[ATL 模組類別](../atl/atl-module-classes.md)  
ATL 7.0 討論新的模組類別。 模組類別會實作基本功能所需的 ATL

[ATL 服務](../atl/atl-services.md)  
涵蓋的一系列實作服務時，會發生的事件。 也討論與開發服務相關的概念。

[ATL 視窗類別](../atl/atl-window-classes.md)  
描述如何建立、 超級類別，以及在 ATL 中的子類別化 windows ATL 視窗類別不是 COM 類別。

[ATL 集合類別](../atl/atl-collection-classes.md)  
描述如何使用陣列和 ATL 中的地圖

[ATL 登錄元件 （登錄器）](../atl/atl-registry-component-registrar.md)  
討論 ATL 指令碼的語法和可置換的參數。 它也會說明如何設定註冊機構的靜態連結。

[使用 ATL 和 C 執行階段程式碼進行程式設計](../atl/programming-with-atl-and-c-run-time-code.md)  
討論將靜態或動態連結到 C 執行階段程式庫 (CRT) 的優點。

[使用 ccombstr 進行程式設計](../atl/programming-with-ccombstr-atl.md)  
討論使用程式設計時，需要注意的幾種情況`CComBSTR`。

[編碼方式參考](../atl/atl-encoding-reference.md)  
提供功能和支援的編碼方式和中的一組常見的網際網路標準，例如十六進位 uuencode UTF8 atlenc.h 中的巨集。

[公用程式參考](../atl/atl-utilities-reference.md)  
提供程式碼，管理路徑與 Url 的形式[CPathT](../atl/reference/cpatht-class.md)並[CUrl](../atl/reference/curl-class.md)。 執行緒集區[CThreadPool](../atl/reference/cthreadpool-class.md)，可用於自己的應用程式。 此程式碼可以找到 atlpath.h 和 atlutil.h 中。

## <a name="related-sections"></a>相關章節

[ATL 範例](../visual-cpp-samples.md)  
提供的描述以及 ATL 範例程式的連結。

[建立 ATL 專案](../atl/reference/creating-an-atl-project.md)  
包含 [ATL 專案精靈] 的相關資訊。

[ATL 控制項精靈](../atl/reference/atl-control-wizard.md)  
討論如何將類別加入。

[屬性化的程式設計](../windows/attributed-programming-concepts.md)  
概述使用屬性來簡化 COM 程式設計的更詳細主題的連結清單。

[ATL 類別概觀](../atl/atl-class-overview.md)  
提供參考資訊和連結至 ATL 類別。

