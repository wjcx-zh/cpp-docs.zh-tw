---
title: 訊息對應 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
ms.openlocfilehash: 92d0b4887127e1803d1d3209a6a1dd51e9a98d15
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496105"
---
# <a name="message-maps-atl"></a>訊息對應 (ATL)

與特定訊息、 命令或通知的訊息對應產生關聯的處理常式函式。 使用 ATL 的[訊息對應巨集](../atl/reference/message-map-macros-atl.md)，您可以指定視窗的訊息對應。 中的視窗程序`CWindowImpl`， `CDialogImpl`，和`CContainedWindowT`其訊息對應的視窗訊息導向。

[訊息處理常式函式](../atl/message-handler-functions.md)接受類型的其他引數`BOOL&`。 這個引數會指出是否已處理訊息，並根據預設將它設定為 TRUE。 為 FALSE，以指出它已不處理訊息，處理常式函式可以將引數。 在此情況下，ATL 會繼續尋找訊息對應中進一步的處理常式函數。 這個引數設為 FALSE，可以先執行一些動作，以回應訊息，並讓預設的處理或另一個處理常式函式，來完成處理訊息。

## <a name="chained-message-maps"></a>鏈結的訊息對應

ATL 也可讓您鏈結訊息對應，將導向至另一個類別中定義的訊息對應處理的訊息。 例如，您可以實作常見訊息處理在個別的類別以鏈結至該類別的所有 windows 提供統一的行為。 您可以鏈結至基底類別或類別的資料成員。

ATL 也支援動態鏈結，可讓您鏈結至另一個物件的訊息對應在執行階段。 若要實作動態鏈結，您必須衍生您的類別，從[CDynamicChain](../atl/reference/cdynamicchain-class.md)。 然後，宣告[CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic)訊息對應中的巨集。 CHAIN_MSG_MAP_DYNAMIC 需要唯一的數字，可識別物件和訊息對應會將鏈結。 您必須定義此唯一的值，透過呼叫`CDynamicChain::SetChainEntry`。

您可以提供的類別衍生自宣告訊息對應中，任何類別鏈結[CMessageMap](../atl/reference/cmessagemap-class.md)。 `CMessageMap` 可讓物件公開給其他物件其訊息對應。 請注意，`CWindowImpl`已經是衍生自`CMessageMap`。

## <a name="alternate-message-maps"></a>替代的訊息對應

最後，ATL 支援替代的訊息對應，以宣告[ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map)巨集。 唯一的數字，您將傳遞給 ALT_MSG_MAP 識別每個替代訊息對應。 使用替代的訊息對應，您可以處理一個 map 中的多個視窗的訊息。 請注意，根據預設，`CWindowImpl`不會使用替代的訊息對應。 若要新增這項支援，請覆寫`WindowProc`方法，在您`CWindowImpl`-衍生類別並呼叫`ProcessWindowMessage`使用訊息對應識別項。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)

