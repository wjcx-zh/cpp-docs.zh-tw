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
ms.openlocfilehash: 5bc17bfc415576d50c84e880bef955e49d926c86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595555"
---
# <a name="atl-com-property-pages"></a>ATL COM 屬性頁

COM 屬性頁來設定屬性中提供的使用者介面 （或呼叫的方法） 的一或多個 COM 物件。 屬性頁會使用廣泛的 ActiveX 控制項來提供豐富的使用者介面，讓控制項的屬性，以在設計階段進行設定。

屬性頁是 COM 物件實作[IPropertyPage](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage)或是[IPropertyPage2](/windows/desktop/api/ocidl/nn-ocidl-ipropertypage2)介面。 這些介面提供方法，可讓頁面與相關聯`site`（COM 物件，表示頁面的容器） 和一些*物件*就會呼叫其方法，以回應變更 （COM 物件使用者所做的屬性頁）。 屬性頁容器會負責向頁面時顯示或隱藏其使用者介面，以及何時將變更套用到使用者所做的基礎物件的屬性頁面介面上呼叫方法。

每個屬性頁可以建置完全獨立的可設定其屬性的物件。 所有這些屬性頁需要的只是了解特定的 「 介面 」 （或稱 「 的介面集 」），並提供使用者介面的介面上呼叫方法。

如需詳細資訊，請參閱 <<c0> [ 屬性工作表和屬性頁](/windows/desktop/com/property-sheets-and-property-pages)Windows SDK 中。

## <a name="in-this-section"></a>本節內容

[指定屬性頁](../atl/specifying-property-pages.md)<br/>
列出指定您的控制項屬性頁的步驟，並顯示範例類別。

[實作屬性頁](../atl/implementing-property-pages.md)<br/>
列出的步驟來實作屬性頁，包括覆寫的方法。 逐步解說 ATLPages 範例程式為基礎的完整範例。

## <a name="related-sections"></a>相關章節

[ATLPages 範例](../visual-cpp-samples.md)<br/>
ATLPages 範例中，實作屬性頁，使用的範例摘要`IPropertyPageImpl`。

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)

