---
title: Automation 用戶端
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 30511ec6c9f0e00f4cec51e00f85ea5e32453327
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465490"
---
# <a name="automation-clients"></a>Automation 用戶端

Automation 可讓您的應用程式操作另一個應用程式中實作的物件，或者公開物件，以便可以操作該物件。 Automation 用戶端是可以操作公開的物件屬於另一個應用程式的應用程式。 會將物件公開的應用程式稱為 Automation 伺服程式。 用戶端存取這些物件的屬性和函式操控伺服器應用程式的物件。

### <a name="types-of-automation-clients"></a>Automation 用戶端的類型

有兩種類型的 Automation 用戶端：

- 用戶端，以動態方式 （在執行階段） 中取得的屬性和作業之伺服器的相關資訊。

- 擁有靜態資訊 （在編譯時期提供），指定的屬性和作業之伺服器的用戶端。

第一類的用戶端取得有關伺服器的方法和屬性的資訊，藉由查詢 OLE 系統`IDispatch`機制。 雖然它是動態的用戶端，請使用適當`IDispatch`很難用於靜態的用戶端，其中的物件被驅動必須知道在編譯時間。 Microsoft Foundation classes 的靜態繫結的用戶端，提供[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)類別。

靜態繫結的用戶端會使用用戶端應用程式中的 proxy 類別，以靜態方式連結。 這個類別提供伺服器應用程式的屬性和作業的型別安全 c + + 的封裝。

此類別`COleDispatchDriver`提供自動化的用戶端的主要支援。 使用**加入新項目** 對話方塊中，您會建立一個衍生自類別`COleDispatchDriver`。

然後，您會指定描述的屬性和函式的伺服器應用程式的物件型別程式庫檔案。 [加入項目] 對話方塊中讀取此檔案，並建立`COleDispatchDriver`-衍生的類別，與您的應用程式可以存取 c + + 中的伺服器應用程式的物件型別安全的方式呼叫的成員函式。 其他功能會繼承自`COleDispatchDriver`簡化呼叫適當的 Automation 伺服器的程序。

### <a name="handling-events-in-automation-clients"></a>在 Automation 用戶端中處理事件

如果您想要在您的自動化用戶端中處理事件，您需要新增接收器介面。 MFC 提供新增接收器介面，ActiveX 控制項，但支援其他 COM 伺服器的精靈支援。

## <a name="see-also"></a>另請參閱

[Automation 用戶端：使用型別程式庫](../mfc/automation-clients-using-type-libraries.md)<br/>
[Automation](../mfc/automation.md)<br/>
[MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)

