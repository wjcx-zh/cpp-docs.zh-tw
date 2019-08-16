---
title: ATL 連接點
ms.date: 11/04/2016
helpviewer_keywords:
- connections, connection points
- ATL, connection points
- connection points [C++], about connection points
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
ms.openlocfilehash: df69496a6d245702a9598d684b25122ca55b1e6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491804"
---
# <a name="atl-connection-points"></a>ATL 連接點

可連接物件是指支援輸出介面的物件。 輸出介面可讓物件與用戶端通訊。 針對每個輸出介面，可連接物件都會公開一個連接點。 每個輸出介面都是由稱為接收 (sink) 的物件上的用戶端所實作。

![連接點](../atl/media/vc2zw31.gif "連接點")

每個連接點都支援[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)介面。 可連線物件會透過[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)介面公開其連接點給用戶端。

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
