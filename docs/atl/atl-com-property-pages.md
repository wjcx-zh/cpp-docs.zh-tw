---
title: ATL COM 屬性頁
ms.date: 11/04/2016
helpviewer_keywords:
- property pages, COM
- ATL COM objects
- COM property pages
- property pages, ATL
- COM objects, ATL
- ATL property pages
ms.assetid: 663c7caa-2e5e-4b5c-b8ea-fd434ceb1654
ms.openlocfilehash: f6f549388e69e9549c64645de758d92822205fd5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491862"
---
# <a name="atl-com-property-pages"></a>ATL COM 屬性頁

COM 屬性頁提供一個使用者介面, 可用於設定一個或多個 COM 物件的屬性 (或呼叫方法)。 ActiveX 控制項廣泛使用屬性頁來提供豐富的使用者介面, 允許在設計階段設定控制項屬性。

屬性頁是執行[IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)或[IPROPERTYPAGE2](/windows/win32/api/ocidl/nn-ocidl-ipropertypage2)介面的 COM 物件。 這些介面提供的方法可讓頁面與`site` (代表頁面容器的 com 物件) 和數個*物件*(com 物件, 其方法會被呼叫以回應使用者對屬性頁)。 屬性頁容器負責在屬性頁介面上呼叫方法, 以告知頁面何時要顯示或隱藏其使用者介面, 以及將使用者所做的變更套用至基礎物件的時機。

每個屬性頁都可以完全獨立地建立, 而這些物件可以設定其屬性。 屬性頁所需的全部都是瞭解特定介面 (或一組介面), 並提供使用者介面來呼叫該介面上的方法。

如需詳細資訊, 請參閱 Windows SDK 中的[屬性工作表和屬性頁](/windows/win32/com/property-sheets-and-property-pages)。

## <a name="in-this-section"></a>本節內容

[指定屬性頁](../atl/specifying-property-pages.md)<br/>
列出指定控制項的屬性頁, 並顯示範例類別的步驟。

[實作屬性頁](../atl/implementing-property-pages.md)<br/>
列出用來執行屬性頁的步驟, 包括要覆寫的方法。 會逐步引導您完成以 ATLPages 範例程式為基礎的完整範例。

## <a name="related-sections"></a>相關章節

[ATLPages 範例](../overview/visual-cpp-samples.md)<br/>
ATLPages 範例的範例摘要, 會使用`IPropertyPageImpl`來執行屬性頁。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)
