---
title: "訊息對應 (ATL) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e708fea75c594c7bb9504515c80222ad901c335
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="message-maps-atl"></a>訊息對應 (ATL)
與特定訊息、 命令或通知的訊息對應產生關聯的處理常式函式。 使用 ATL 的[訊息對應巨集](../atl/reference/message-map-macros-atl.md)，您可以指定視窗的訊息對應。 中的視窗程序`CWindowImpl`， `CDialogImpl`，和`CContainedWindowT`導向至其訊息對應視窗的訊息。  
  
 [訊息處理函式](../atl/message-handler-functions.md)接受類型的其他引數`BOOL&`。 這個引數會指出是否已處理訊息，並設定為`TRUE`預設。 處理常式函式可以將引數設`FALSE`表示它有未處理的訊息。 在此情況下，ATL 將會繼續尋找訊息對應中進一步的處理常式函數。 藉由設定這個引數為`FALSE`，您可以先執行一些動作以回應訊息，並讓預設處理或另一個處理常式函式，來完成處理訊息。  
  
## <a name="chained-message-maps"></a>鏈結的訊息對應  
 ATL 也可讓您鏈結訊息對應，以將導向至另一個類別中定義的訊息對應處理的訊息。 例如，您可以實作一般訊息在個別的類別中處理鏈結至該類別的所有視窗提供統一的行為。 您可以鏈結的基底類別或類別的資料成員。  
  
 ATL 也支援動態鏈結，可讓您可鏈結另一個物件的訊息對應到在執行階段。 若要實作動態鏈結，您必須衍生您的類別從[CDynamicChain](../atl/reference/cdynamicchain-class.md)。 然後，宣告[CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic)中訊息對應巨集。 `CHAIN_MSG_MAP_DYNAMIC`需要識別的物件和訊息對應會將鏈結的唯一數字。 您必須定義此唯一的值，透過呼叫`CDynamicChain::SetChainEntry`。  
  
 您可以鏈結會宣告訊息對應，任何類別提供的類別衍生自[CMessageMap](../atl/reference/cmessagemap-class.md)。 `CMessageMap`讓物件公開至其他物件其訊息對應。 請注意，`CWindowImpl`已經衍生自`CMessageMap`。  
  
## <a name="alternate-message-maps"></a>替代的訊息對應  
 最後，ATL 支援替代的訊息對應，以宣告[ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map)巨集。 每個替代訊息對應由唯一數字，您將傳遞給`ALT_MSG_MAP`。 使用替代訊息對應，您可以處理之訊息的一個對應中的多個視窗。 請注意，根據預設，`CWindowImpl`不會使用替代的訊息對應。 若要新增此支援，請覆寫`WindowProc`方法在您`CWindowImpl`-衍生類別並呼叫`ProcessWindowMessage`訊息對應識別碼。  
  
## <a name="see-also"></a>請參閱  
 [實作視窗](../atl/implementing-a-window.md)

