---
title: 'Catlservicemodulet:: Start 函式'
ms.date: 11/04/2016
f1_keywords:
- CServiceModule.Start
- CServiceModule::Start
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 806cd8ec353e2111d249472fb9aa885e7548baab
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265154"
---
# <a name="catlservicemoduletstart-function"></a>Catlservicemodulet:: Start 函式

當服務執行時，`_tWinMain`呼叫`CAtlServiceModuleT::WinMain`，接著呼叫`CAtlServiceModuleT::Start`。

`CAtlServiceModuleT::Start` 設定陣列`SERVICE_TABLE_ENTRY`對應至其啟動函式的每個服務的結構。 Win32 API 函式，然後傳遞此陣列[StartServiceCtrlDispatcher](/windows/desktop/api/winsvc/nf-winsvc-startservicectrldispatchera)。 理論上，一個 EXE 可以處理多個服務，且陣列可能有多個`SERVICE_TABLE_ENTRY`結構。 目前，不過，ATL 產生服務支援每個 EXE 的只有一個服務。 因此，陣列有一個項目，其中包含服務名稱和`_ServiceMain`與啟始函式。 `_ServiceMain` 靜態成員函式`CAtlServiceModuleT`呼叫非靜態成員函式， `ServiceMain`。

> [!NOTE]
>  失敗的`StartServiceCtrlDispatcher`連接到服務控制管理員 (SCM) 可能表示做為服務，不執行程式。 在此情況下，程式會呼叫`CAtlServiceModuleT::Run`直接，以便程式可以當做本機伺服器執行。 如需為本機伺服器執行程式的詳細資訊，請參閱[偵錯秘訣](../atl/debugging-tips.md)。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
