---
title: 'Catlservicemodulet:: Handler 函式'
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Handler
- CServiceModule.Handler
- Handler
helpviewer_keywords:
- Handler method
ms.assetid: 14db5f2a-be87-4774-a296-445cb6fc7b2e
ms.openlocfilehash: e344fd36ad6c70a80486eef6a10eacd8a88a2baf
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273370"
---
# <a name="catlservicemodulethandler-function"></a>Catlservicemodulet:: Handler 函式

`CAtlServiceModuleT::Handler` 會擷取服務的狀態，並為它提供各種指示 （例如停止或暫停） 的服務控制管理員 (SCM) 呼叫的常式。 SCM 會傳遞至作業程式碼`Handler`來指出應該執行的服務。 預設 ATL 產生服務只會處理停止指令。 如果 SCM 通過 stop 指令，服務會通知程式即將停止 SCM。 服務接著會呼叫`PostThreadMessage`quit 的訊息張貼至本身。 這將終止訊息迴圈，服務會完全關閉。

若要處理的詳細指示，您需要變更`m_status`中的資料成員初始化`CAtlServiceModuleT`建構函式。 此資料成員會指示 SCM 哪一個按鈕，讓服務選取服務 控制台應用程式中時。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Handler](../atl/reference/catlservicemodulet-class.md#handler)
