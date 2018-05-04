---
title: CAtlServiceModuleT::ServiceMain 函式 |Microsoft 文件
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
ms.openlocfilehash: 9936090793890b1e33f0d5e29787d65f378afa84
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="catlservicemoduletservicemain-function"></a>CAtlServiceModuleT::ServiceMain 函式
服務控制管理員 (SCM) 呼叫`ServiceMain`當您開啟 服務控制台應用程式，選取服務，然後按一下**啟動**。  
  
 SCM 之後呼叫`ServiceMain`，服務必須提供 SCM 處理常式函式。 此函式可讓 SCM 取得服務的狀態並傳遞 （例如暫停或停止） 的特定指示。 SCM 會取得此函式時，服務則傳遞 **_Handler** Win32 API 函式[RegisterServiceCtrlHandler](http://msdn.microsoft.com/library/windows/desktop/ms685054)。 (**_Handler**是靜態成員函式呼叫非靜態成員函式的[處理常式](../atl/reference/catlservicemodulet-class.md#handler)。)  
  
 在啟動時，服務應該也要通知的 SCM 它目前的狀態。 其做法是傳遞**SERVICE_START_PENDING** Win32 API 函式[SetServiceStatus](http://msdn.microsoft.com/library/windows/desktop/ms686241)。  
  
 `ServiceMain` 然後呼叫`CAtlExeModuleT::InitializeCom`，呼叫 Win32 API 函式[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)。 根據預設，`InitializeCom`傳遞**COINIT_MULTITHREADED**函式的旗標。 這個旗標會指出程式是為無限制執行緒的伺服器。  
  
 現在，`CAtlServiceModuleT::Run`呼叫以執行服務的主要工作。 **執行**會繼續執行直到服務已停止。  
  
## <a name="see-also"></a>另請參閱  
 [服務](../atl/atl-services.md)   
 [CAtlServiceModuleT::ServiceMain](../atl/reference/catlservicemodulet-class.md#servicemain)

