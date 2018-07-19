---
title: 為本機伺服器執行程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae2e44ba51a878d293ad5b497a1638cc9d7dc76
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848479"
---
# <a name="running-the-program-as-a-local-server"></a>為本機伺服器執行程式
如果以服務方式執行該程式是不太方便，您可以暫時變更登錄，以便做為一般的本機伺服器執行程式。 只重新命名`LocalService`值在您應用程式識別碼之下`_LocalService`，並確保`LocalServer32`已正確設定您的 CLSID 下的索引鍵。 (請注意，若要指定您的應用程式應在不同的電腦上執行使用 DCOMCNFG 將重新命名您`LocalServer32`機碼`_LocalServer32`。)執行您的程式，因為在本機伺服器會會在啟動幾秒，因為呼叫`StartServiceCtrlDispatcher`在`CAtlServiceModuleT::Start`失敗之前的幾秒。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯提示](../atl/debugging-tips.md)

