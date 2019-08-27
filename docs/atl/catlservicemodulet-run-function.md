---
title: 'CAtlServiceModuleT:: Run 函式'
ms.date: 11/04/2016
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 0c35020996852731a8f22c15860d4cceb7a8bdb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491524"
---
# <a name="catlservicemoduletrun-function"></a>CAtlServiceModuleT:: Run 函式

`Run`包含`PreMessageLoop`、 `RunMessageLoop`和的呼叫。`PostMessageLoop` 在呼叫之後, `PreMessageLoop`會先儲存服務的執行緒識別碼。 服務會使用此識別碼來關閉本身, 方法是使用 WIN32 API 函式[PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew)傳送 WM_QUIT 訊息。

`PreMessageLoop`然後呼叫`InitializeSecurity`。 根據預設, `InitializeSecurity`會呼叫[CoInitializeSecurity](/windows/win32/api/combaseapi/nf-combaseapi-coinitializesecurity) , 並將安全描述項設定為 Null, 這表示任何使用者都可以存取您的物件。

如果您不想讓服務指定自己的安全性, 請覆寫`PreMessageLoop`並不要呼叫`InitializeSecurity`, 然後 COM 會從登錄判斷安全性設定。 設定登錄設定的便利方式是使用本節稍後討論的[dcomcnfg.exe](../atl/dcomcnfg.md)公用程式。

一旦指定了安全性, 就會向 COM 註冊物件, 讓新的用戶端可以連接到程式。 最後, 此程式會告訴服務控制管理員 (SCM) 它正在執行, 而且程式會進入訊息迴圈。 程式會持續執行, 直到服務關閉時張貼 quit 訊息為止。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)<br/>
[CSecurityDesc 類別](../atl/reference/csecuritydesc-class.md)<br/>
[CSid 類別](../atl/reference/csid-class.md)<br/>
[CDacl 類別](../atl/reference/cdacl-class.md)<br/>
[CAtlServiceModuleT::Run](../atl/reference/catlservicemodulet-class.md#run)
