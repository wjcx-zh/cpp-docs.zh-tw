---
title: Automation 伺服程式
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 39e870db2f5476a630a8ed3bc68944dbb164d469
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305129"
---
# <a name="automation-servers"></a>Automation 伺服程式

Automation 可讓您的應用程式操作另一個應用程式中實作的物件，或者公開物件，以便可以操作該物件。 Automation 伺服程式是對其他應用程式公開可程式化物件 （稱為 Automation 物件） 的應用程式 (稱為[Automation 用戶端](../mfc/automation-clients.md))。 Automation 伺服器有時稱為 Automation 元件。

公開 Automation 物件可讓用戶端直接存取物件以自動化某些程序以及伺服器所提供的某些功能。 以這種方式公開物件在應用程式為其他應用程式提供很有用的功能時會很有幫助。 例如，文書處理器可能會公開其拼字檢查功能，讓其他程式可以使用它。 公開物件可讓廠商使用其他應用程式的現成功能，以改善其應用程式的功能。

這些 Automation 物件使用屬性與方法做為其外部介面。 屬性是 Automation 物件的具名屬性。 屬性與 C++ 類別的資料成員類似。 方法是在 Automation 物件上運作的函式。 方法與 C++ 類別的公用成員函式類似。

> [!NOTE]
>  雖然屬性與 C++ 資料成員類似，但這些屬性無法進行直接存取。 若要提供透明的存取，請在具有一對取得/設定成員函式的 Automation 物件中設定一個內部變數，以存取它們。

透過共用、明確定義的介面來公開應用程式功能，使得 Automation 可以在如 Microsoft Visual Basic 的單一一般程式語言中建置應用程式，而不是在不同的應用程式專屬巨集語言中進行存取。

##  <a name="_core_support_for_automation_servers"></a> 支援 Automation 伺服器

Visual C++ 和 MFC 架構為 Automation 伺服器提供廣泛的支援。 其中處理了許多建立 Automation 伺服器的額外工作，因此，您可以專注在應用程式的功能上。

架構支援 Automation 的主要機制是分派對應，一組展開成宣告及呼叫所需 OLE 公開方法和屬性的巨集。 典型的分派對應如下所示：

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

[屬性] 視窗和 [類別] 檢視可協助維護分派對應。 當您將新的方法或屬性加入至類別時，Visual C++ 會加入對應的 `DISP_FUNCTION` 或 `DISP_PROPERTY` 巨集與表示類別名稱、方法的外部和內部名稱或屬性和資料類型的參數。

**加入類別**對話方塊也簡化了 Automation 類別的宣告和管理其屬性和作業。 當您使用 [加入類別] 對話方塊將類別加入至專案時，您會指定它的基底類別。 如果基底類別允許 Automation，[加入類別] 對話方塊會顯示一些控制項，可供您用來指定新的類別是否應支援 Automation、它是否「可建立 OLE」(即是否可在 COM 用戶端的要求上建立類別的物件)，以及要使用的 COM 用戶端的外部名稱。

**加入類別**對話方塊接著會建立在類別宣告，包括適當的巨集之 OLE 功能，您已指定。 它也會加入類別成員函式實作的基本架構程式碼。

[MFC 應用程式精靈] 簡化了取得您的 Automation 伺服器應用程式所需的步驟。 如果您選取**自動化**核取方塊，從**進階功能**頁面上，將您的應用程式的 MFC 應用程式精靈`InitInstance`函式來註冊您的自動化所需的呼叫物件，並執行您的應用程式當做 Automation 伺服器。

### <a name="what-do-you-want-to-do"></a>您要做什麼

- [深入了解自動化用戶端](../mfc/automation-clients.md)

- [深入了解 CCmdTarget 類別](../mfc/reference/ccmdtarget-class.md)

- [深入了解 COleDispatchDriver 類別](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>另請參閱

[Automation](../mfc/automation.md)<br/>
[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)
