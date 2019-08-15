---
title: 'CAtlServiceModuleT:: Start 函式'
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: e6de15f40e89bfffba504db04ee7a16b2a68cac9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491670"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT:: Start 函式

當服務執行時, `_tWinMain`會呼叫`CAtlServiceModuleT::WinMain` `CAtlServiceModuleT::Start`, 然後再呼叫。

`CAtlServiceModuleT::Start`設定`SERVICE_TABLE_ENTRY`結構的陣列, 以將每個服務對應至其啟動函數。 然後, 此陣列會傳遞至 WIN32 API 函式[StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw)。 理論上, 一個 EXE 可以處理多個服務, 而陣列可以有`SERVICE_TABLE_ENTRY`多個結構。 不過, 目前 ATL 產生的服務只支援每個 EXE 一個服務。 因此, 陣列具有單一專案, 其中包含服務名稱和`_ServiceMain`作為啟動函數。 `_ServiceMain`是的靜態成員`CAtlServiceModuleT`函式, `ServiceMain`會呼叫非靜態成員函式。

> [!NOTE]
>  `StartServiceCtrlDispatcher`若無法連接到服務控制管理員 (SCM), 可能表示程式未以服務的形式執行。 在此情況下, 程式會`CAtlServiceModuleT::Run`直接呼叫, 讓程式可以當做本機伺服器來執行。 如需以本機伺服器的形式執行程式的詳細資訊, 請參閱[偵錯工具提示](../atl/debugging-tips.md)。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::Start](../atl/reference/catlservicemodulet-class.md#start)
