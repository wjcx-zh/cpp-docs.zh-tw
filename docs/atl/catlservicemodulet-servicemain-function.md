---
title: 'Catlservicemodulet:: Servicemain 函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- ServiceMain
- CServiceModule::ServiceMain
- CServiceModule.ServiceMain
dev_langs:
- C++
helpviewer_keywords:
- ServiceMain method
ms.assetid: f21408c1-1919-4dec-88d8-bf5b39ac9808
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 746a7c9d95d629329fb0f47705f61c5f0753a662
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203678"
---
# <a name="catlservicemoduletservicemain-function"></a>Catlservicemodulet:: Servicemain 函式
服務控制管理員 (SCM) 會呼叫`ServiceMain`當您開啟 [服務] 控制台應用程式，選取服務，然後按一下**啟動**。  
  
 SCM 之後會呼叫`ServiceMain`，服務必須讓 SCM 處理常式函式。 此函式可讓 SCM 取得服務的狀態並傳遞 （例如暫停或停止） 的特定指示。 SCM 會取得此函式，當服務通過`_Handler`Win32 API 函式[RegisterServiceCtrlHandler](/windows/desktop/api/winsvc/nf-winsvc-registerservicectrlhandlera)。 (`_Handler`靜態成員函式呼叫非靜態成員函式[處理常式](../atl/reference/catlservicemodulet-class.md#handler)。)  
  
 在啟動時，服務也應該通知 SCM，它目前的狀態。 其做法是將傳遞至 Win32 API 函式的 SERVICE_START_PENDING [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)。  
  
 `ServiceMain` 然後呼叫`CAtlExeModuleT::InitializeCom`，它會呼叫 Win32 API 函式[CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex)。 根據預設， `InitializeCom` COINIT_MULTITHREADED 旗標傳遞至函數。 此旗標會指出程式是無限制執行緒的伺服器。  
  
 現在，`CAtlServiceModuleT::Run`呼叫來執行服務的主要工作。 `Run` 會繼續執行，直到服務已停止。  
  
## <a name="see-also"></a>另請參閱  
 [服務](../atl/atl-services.md)   
 [Catlservicemodulet:: Servicemain](../atl/reference/catlservicemodulet-class.md#servicemain)

