---
title: ATL 連接點
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: 520537f5d562450dc4ea2a5e5a0c68af513da509
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175052"
---
# <a name="atl-connection-points"></a>ATL 連接點

可連接物件是指支援輸出介面的物件。 輸出介面可讓物件與用戶端通訊。 針對每個輸出介面，可連接物件都會公開一個連接點。 每個輸出介面都是由稱為接收 (sink) 的物件上的用戶端所實作。

![連接點](../atl/media/vc2zw31.gif "連接點")

每個連接點支援[IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint)介面。 可連接物件會公開至用戶端透過其連接點[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)介面。

## <a name="in-this-section"></a>本節內容

[ATL 連接點類別](../atl/atl-connection-point-classes.md)<br/>
簡短說明支援連接點的 ATL 類別。

[將連接點新增至物件](../atl/adding-connection-points-to-an-object.md)<br/>
概述用來將連接點加入物件的步驟。

[ATL 連接點範例](../atl/atl-connection-point-example.md)<br/>
提供宣告連接點的範例。

## <a name="related-sections"></a>相關章節

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供有關如何使用 Active Template Library 進行程式設計的概念性主題連結。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)

