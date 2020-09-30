---
title: Active Template Library (ATL) 概念
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: c87eedff5b6ce7d906c05ac0678425af575f0af8
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504269"
---
# <a name="active-template-library-atl-concepts"></a>Active Template Library (ATL) 概念

Active Template Library (ATL) 是一組以範本為基礎的 C++ 類別，可讓您建立小型、快速的元件物件模型 (COM) 物件。 它具有主要 COM 功能的特殊支援，包括內建實作、雙重介面、標準 COM 列舉程式介面、連接點、Tear-Off 介面和 ActiveX 控制項。

如果您執行大量的 ATL 程式設計，您可以深入了解 COM 和 .NET 屬性，因為其設計目的就是要簡化 COM 程式設計。 如需詳細資訊，請參閱[屬性化程式設計](../windows/attributes/cpp-attributes-com-net.md)。 (COM 和 .NET 屬性不應與 C++ 標準中的 \[\[attribute]] 功能混淆。)

## <a name="in-this-section"></a>本節內容

[COM 和 ATL 簡介](introduction-to-com-and-atl.md)<br/>
介紹元件物件模型 (COM) 背後的主要概念。 本文也將簡短說明 ATL 為何及其使用時機。

[ATL COM 物件的基本概念](fundamentals-of-atl-com-objects.md)<br/>
討論各種 ATL 類別之間的關聯性，以及這些類別的實作方式。

[雙重介面和 ATL](dual-interfaces-and-atl.md)<br/>
從 ATL 觀點說明雙重介面。

[ATL 集合和枚舉器](atl-collections-and-enumerators.md)<br/>
說明如何在 ATL 中實作和建立集合和列舉程式。

[複合控制項基本概念](atl-composite-control-fundamentals.md)<br/>
提供建立複合控制項的逐步指示。 複合控制項是一種可包含其他 ActiveX 控制項或 Windows 控制項的 ActiveX 控制項。

[ATL 控制項內含專案常見問題](atl-control-containment-faq.md)<br/>
說明以 ATL 裝載控制項的相關基本問題。

[ATL COM 屬性頁](atl-com-property-pages.md)<br/>
說明如何指定及實作 COM 屬性頁。

[DHTML 控制項的 ATL 支援](atl-support-for-dhtml-controls.md)<br/>
提供建立 DHTML 控制項的逐步指示。

[ATL 連接點](atl-connection-points.md)<br/>
說明連接點是什麼，以及 ATL 如何加以實作。

[事件處理和 ATL](event-handling-and-atl.md)<br/>
說明您使用 ATL 的 [IDispEventImpl](reference/idispeventimpl-class.md) 和 [IDispEventSimpleImpl](reference/idispeventsimpleimpl-class.md) 類別來處理 COM 事件時所需執行的步驟。

[ATL 和無限制執行緒封送處理器](atl-and-the-free-threaded-marshaler.md)<br/>
提供可讓您的類別彙總無限制執行緒封送處理器 (FTM) 的「ATL 簡單物件精靈」選項的詳細資料。

[指定專案的執行緒模型](specifying-the-threading-model-for-a-project-atl.md)<br/>
說明哪些巨集可用來控制與您專案中的執行緒有關的執行階段效能。

[ATL 模組類別](atl-module-classes.md)<br/>
討論 ATL 7.0 的新模組類別。 模組類別會實作 ATL 所需的基本功能。

[ATL 服務](atl-services.md)<br/>
說明在實作服務時會發生的一系列事件。 此外也會討論與開發服務有關的一些概念。

[ATL 視窗類別](atl-window-classes.md)<br/>
說明如何在 ATL 中建立 Superclass 和子類別視窗。 ATL 視窗類別不是 COM 類別。

[ATL 集合類別](atl-collection-classes.md)<br/>
說明如何在 ATL 中使用陣列和對應。

[ATL 登錄元件 (登錄器)](atl-registry-component-registrar.md)<br/>
討論 ATL 指令碼語法和可置換的參數。 此外也會說明如何設定登錄器的靜態連結。

[使用 ATL 和 C 執行時間程式碼進行程式設計](programming-with-atl-and-c-run-time-code.md)<br/>
討論以靜態或動態方式連結至 C 執行階段程式庫 (CRT) 的優點。

[使用 CComBSTR 進行程式設計](programming-with-ccombstr-atl.md)<br/>
討論使用 `CComBSTR` 進行程式設計時必須注意的幾種情況。

[編碼方式參考](atl-encoding-reference.md)<br/>
提供在多種常用的網際網路標準 (例如 atlenc.h 中的 UUEncode、十六進位和 UTF8) 中支援編碼的功能和巨集。

[公用程式參考](atl-utilities-reference.md)<br/>
提供程式碼，用以管理 [CPathT](reference/cpatht-class.md) 和 [CUrl](reference/curl-class.md) 形式的路徑和 URL。 執行緒集區 [CThreadPool](reference/cthreadpool-class.md) 可用於您自己的應用程式。 此程式碼可以在 atlpath.h 和 atlutil.h 中找到。

## <a name="related-sections"></a>相關章節

[ATL 教學課程](active-template-library-atl-tutorial.md)<br/>
引導您建立控制項，並示範程序中的一些 ATL 基本概念。

[ATL 範例](../overview/visual-cpp-samples.md)<br/>
提供 ATL 範例程式連結的描述。

[建立 ATL 專案](reference/creating-an-atl-project.md)<br/>
包含「ATL 專案精靈」的相關資訊。

[ATL 控制項精靈](reference/atl-control-wizard.md)<br/>
討論如何新增類別。

[屬性化程式設計](../windows/attributes/cpp-attributes-com-net.md)<br/>
概述如何使用屬性來簡化 COM 程式設計，並提供詳細主題的連結清單。

[ATL 類別總覽](atl-class-overview.md)<br/>
提供 ATL 類別的參考資訊和連結。
