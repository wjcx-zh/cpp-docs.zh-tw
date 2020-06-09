---
title: Automation 用戶端
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 9c34f6fccd06635dfb686e6eb1f2cf895bb86989
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626074"
---
# <a name="automation-clients"></a>Automation 用戶端

Automation 可讓您的應用程式操作另一個應用程式中實作的物件，或者公開物件，以便可以操作該物件。 Automation 用戶端是一種應用程式，可以操控屬於另一個應用程式的公開物件。 公開物件的應用程式稱為 Automation 伺服器。 用戶端會藉由存取這些物件的屬性和函式來操作伺服器應用程式的物件。

### <a name="types-of-automation-clients"></a>自動化用戶端的類型

自動化用戶端有兩種類型：

- 以動態方式（在執行時間）取得伺服器屬性和作業相關資訊的用戶端。

- 擁有指定伺服器屬性和作業之靜態資訊（在編譯時期提供）的用戶端。

第一種類型的用戶端會藉由查詢 OLE 系統的機制，取得伺服器的方法和屬性的相關資訊 `IDispatch` 。 雖然它適合用於動態用戶端，但很 `IDispatch` 難以用於靜態用戶端，在此情況下，所驅動的物件必須在編譯階段為已知。 若為靜態系結用戶端，Microsoft Foundation 類別會提供[COleDispatchDriver](reference/coledispatchdriver-class.md)類別。

靜態系結用戶端會使用以靜態方式與用戶端應用程式連結的 proxy 類別。 這個類別會為伺服器應用程式的屬性和作業提供型別安全的 c + + 封裝。

類別會 `COleDispatchDriver` 為自動化的用戶端提供主體支援。 使用 [**加入新專案**] 對話方塊，您可以建立衍生自的類別 `COleDispatchDriver` 。

接著，您可以指定類型程式庫檔案，描述伺服器應用程式物件的屬性和功能。 [加入專案] 對話方塊會讀取這個檔案，並建立 `COleDispatchDriver` 衍生類別，其中包含您的應用程式可以呼叫的成員函式，以型別安全的方式存取 c + + 中伺服器應用程式的物件。 繼承自的其他功能會 `COleDispatchDriver` 簡化呼叫適當 Automation 伺服器的程式。

### <a name="handling-events-in-automation-clients"></a>處理 Automation 用戶端中的事件

如果您想要在 automation 用戶端中處理事件，您需要新增接收介面。 MFC 提供的 wizard 支援可新增 ActiveX 控制項的接收介面，但不支援其他 COM 伺服器。

## <a name="see-also"></a>另請參閱

[Automation 用戶端：使用型別程式庫](automation-clients-using-type-libraries.md)<br/>
[自動化](automation.md)<br/>
[MFC 應用程式精靈](reference/mfc-application-wizard.md)
