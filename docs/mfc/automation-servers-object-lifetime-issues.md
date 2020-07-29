---
title: Automation 伺服程式：物件存留期問題
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: 8031902318a091b0ed5f340b454a14b9df195069
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225081"
---
# <a name="automation-servers-object-lifetime-issues"></a>Automation 伺服程式：物件存留期問題

當 Automation 用戶端建立或啟用 OLE 項目時，伺服器會傳遞該物件的指標給用戶端。 用戶端會透過呼叫 OLE 函數[IUnknown：： AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)來建立物件的參考。 在用戶端呼叫[IUnknown：： Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)之前，此參考會生效。 （使用 MFC 程式庫的 OLE 類別所撰寫的用戶端應用程式不需要進行這些呼叫; 架構會這麼做）。OLE 系統和伺服器本身可能會建立物件的參考。 只要物件的外部參考仍然有效，伺服器就不應終結物件。

架構會針對衍生自[CCmdTarget](reference/ccmdtarget-class.md)的任何伺服器物件，維護其參考數目的內部計數。 當 Automation 用戶端或其他實體加入或釋放對物件的參考時，便會更新這個計數。

當參考計數變成0時，架構會呼叫虛擬函數[CCmdTarget：： OnFinalRelease](reference/ccmdtarget-class.md#onfinalrelease)。 此函式的預設實作用會呼叫 **`delete`** 運算子來刪除此物件。

當外部用戶端擁有對應用程式物件的參考時，MFC 程式庫會提供額外的功能以控制應用程式行為。 除了維護對每個物件的參考計數之外，伺服器還會維護使用中物件的全域計數。 全域函式[AfxOleLockApp](reference/application-control.md#afxolelockapp)和[AfxOleUnlockApp](reference/application-control.md#afxoleunlockapp)會更新應用程式的作用中物件計數。 如果這個計數不為零，則當使用者從系統功能表選擇 [關閉] 或從 [檔案] 功能表選擇 [結束] 時，不會結束應用程式。 相反地，應用程式的主視窗會被隱藏 (但不會被終結)，直到所有暫止的用戶端要求已經完成。 通常，`AfxOleLockApp` 和 `AfxOleUnlockApp` 會分別由支援 Automation 之類別的建構函式和解構函式呼叫。

當用戶端仍然擁有對物件的參考時，某些情況下會強制終止伺服器。 例如，伺服器所依存的資源可能變為無法使用，造成伺服器遇到錯誤。 使用者也可以關閉包含具有參考之其他應用程式物件的伺服器文件。

在 Windows SDK 中，請參閱 `IUnknown::AddRef` 和 `IUnknown::Release` 。

## <a name="see-also"></a>另請參閱

[Automation 伺服器](automation-servers.md)<br/>
[AfxOleCanExitApp](reference/application-control.md#afxolecanexitapp)
