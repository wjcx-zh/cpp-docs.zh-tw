---
title: 'CAtlServiceModuleT:: ServiceMain 函式'
ms.date: 11/04/2016
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
ms.openlocfilehash: b79767d4c1696174f90a325ea152ccc7939ed9fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491715"
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT:: ServiceMain 函式

當您開啟 [服務] 控制台應用`ServiceMain`程式、選取服務, 然後按一下 [**啟動**] 時, 即會呼叫服務控制管理員 (SCM)。

在 scm 呼叫`ServiceMain`之後, 服務必須為 SCM 提供處理常式函式。 此函式可讓 SCM 取得服務的狀態, 並傳遞特定的指示 (例如暫停或停止)。 當服務傳遞`_Handler`至 WIN32 API 函數[RegisterServiceCtrlHandler](/windows/win32/api/winsvc/nf-winsvc-registerservicectrlhandlerw)時, SCM 會取得此函式。 (`_Handler`是呼叫非靜態成員函式[處理常式](../atl/reference/catlservicemodulet-class.md#handler)的靜態成員函式)。

在啟動時, 服務也應該通知 SCM 其目前狀態。 其運作方式是將 SERVICE_START_PENDING 傳遞至 WIN32 API 函式[SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)。

`ServiceMain`然後呼叫`CAtlExeModuleT::InitializeCom`, 其會呼叫 WIN32 API 函式[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)。 根據預設, `InitializeCom`會將 COINIT_MULTITHREADED 旗標傳遞給函式。 此旗標表示程式是無限制執行緒的伺服器。

現在, `CAtlServiceModuleT::Run`會呼叫來執行服務的主要工作。 `Run`會繼續執行, 直到服務停止為止。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)<br/>
[CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)
