---
title: 'Catlservicemodulet:: Run 函式'
ms.date: 11/04/2016
f1_keywords:
- CServiceModule::Run
- CServiceModule.Run
- CSecurityDescriptor
helpviewer_keywords:
- ATL services, security
ms.assetid: 42c010f0-e60e-459c-a63b-a53a24cda93b
ms.openlocfilehash: 3abb6908a64864463c45d8fc4dc24bfc813db586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458653"
---
# <a name="catlservicemoduletrun-function"></a>Catlservicemodulet:: Run 函式

`Run` 包含呼叫`PreMessageLoop`， `RunMessageLoop`，和`PostMessageLoop`。 在被呼叫之後`PreMessageLoop`第一次儲存服務的執行緒 id。 服務會使用此 ID 來傳送 WM_QUIT 訊息使用 Win32 API 函式，就可以將它關閉本身[PostThreadMessage](https://msdn.microsoft.com/library/windows/desktop/ms644946)。

`PreMessageLoop` 然後呼叫`InitializeSecurity`。 根據預設，`InitializeSecurity`呼叫[CoInitializeSecurity](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializesecurity)與安全性描述元設定為 NULL，這表示任何使用者可對您物件的存取。

如果您不想要指定自己的安全性服務，會覆寫`PreMessageLoop`，且不要呼叫`InitializeSecurity`，COM 然後會判斷來自登錄的安全性設定。 若要設定登錄設定方便的方法是使用[DCOMCNFG](../atl/dcomcnfg.md)本章節稍後所討論的公用程式。

安全性指定之後，物件會向 COM，讓新的用戶端可以連線到的程式。 最後，程式執行，而且程式進入的訊息迴圈會告知服務控制管理員 (SCM)。 在服務關閉時將 quit 的訊息張貼之後，直到執行程式。

## <a name="see-also"></a>另請參閱

[服務](../atl/atl-services.md)<br/>
[CSecurityDesc 類別](../atl/reference/csecuritydesc-class.md)<br/>
[CSid 類別](../atl/reference/csid-class.md)<br/>
[CDacl 類別](../atl/reference/cdacl-class.md)<br/>
[Catlservicemodulet:: Run](../atl/reference/catlservicemodulet-class.md#run)

