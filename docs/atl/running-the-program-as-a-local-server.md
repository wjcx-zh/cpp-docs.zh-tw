---
title: 為本機伺服器執行程式
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], running services as local server
- ATL services, running as local servers
ms.assetid: eb9701e6-e2a8-4666-897f-0c893aec8ac7
ms.openlocfilehash: a412814fc5f3900a248f779501e2720b72287e57
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196518"
---
# <a name="running-the-program-as-a-local-server"></a>為本機伺服器執行程式

如果以服務方式執行該程式是不太方便，您可以暫時變更登錄，以便做為一般的本機伺服器執行程式。 只重新命名`LocalService`值在您應用程式識別碼之下`_LocalService`，並確保`LocalServer32`已正確設定您的 CLSID 下的索引鍵。 (請注意，若要指定您的應用程式應在不同的電腦上執行使用 DCOMCNFG 將重新命名您`LocalServer32`機碼`_LocalServer32`。)執行您的程式，因為在本機伺服器會會在啟動幾秒，因為呼叫`StartServiceCtrlDispatcher`在`CAtlServiceModuleT::Start`失敗之前的幾秒。

## <a name="see-also"></a>另請參閱

[偵錯提示](../atl/debugging-tips.md)
