---
title: CAtlServiceModuleT::啟動功能
ms.date: 11/04/2016
helpviewer_keywords:
- Start method
ms.assetid: b5193a23-41bc-42d2-8d55-3eb43dc62238
ms.openlocfilehash: 50054bbb34bcc31a1d11dd8bfab797f98e4e82f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317284"
---
# <a name="catlservicemoduletstart-function"></a>CAtlServiceModuleT::啟動功能

執行服務時,`_tWinMain`呼`CAtlServiceModuleT::WinMain`叫 呼叫 ,`CAtlServiceModuleT::Start`然後呼叫 。

`CAtlServiceModuleT::Start`設置一個`SERVICE_TABLE_ENTRY`結構陣列,將每個服務映射到其啟動函數。 然後,此陣列將傳遞給 Win32 API 函數[StartServiceCtrlDispatcher](/windows/win32/api/winsvc/nf-winsvc-startservicectrldispatcherw)。 理論上,一個 EXE 可以處理多個服務,並且陣`SERVICE_TABLE_ENTRY`列可以 有多個結構。 但是,目前 ATL 生成的服務僅支援每個 EXE 的一個服務。 因此,陣列具有一個包含服務名稱並作為`_ServiceMain`啟動函數的條目。 `_ServiceMain`是呼叫非靜態成員函數`CAtlServiceModuleT`的靜態成員函`ServiceMain`數 。

> [!NOTE]
> `StartServiceCtrlDispatcher`無法連接到服務控制管理員 (SCM) 可能意味著程式未作為服務運行。 在這種情況下,程式直接調用`CAtlServiceModuleT::Run`,以便程式可以作為本地伺服器運行。 有關將應用程式作為本地端伺服器執行的詳細資訊,請參閱[除錯提示](../atl/debugging-tips.md)。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)<br/>
[CAtlService 模組T::開始](../atl/reference/catlservicemodulet-class.md#start)
