---
title: Automation 用戶端 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 52eaae8074b984da32e115e779724fa86602b8f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342487"
---
# <a name="automation-clients"></a>Automation 用戶端
Automation 可讓您的應用程式操作另一個應用程式中實作的物件，或者公開物件，以便可以操作該物件。 Automation 用戶端是可以操作公開的物件屬於另一個應用程式的應用程式。 公開物件的應用程式稱為 Automation 伺服器。 用戶端會藉由存取這些物件的屬性和函式管理伺服器應用程式的物件。  
  
### <a name="types-of-automation-clients"></a>Automation 用戶端的類型  
 有兩種類型的 Automation 用戶端：  
  
-   用戶端 （在執行階段動態） 取得的屬性和伺服器作業的相關資訊。  
  
-   用戶端擁有靜態資訊 （在編譯時期提供），指定的屬性和作業的伺服器。  
  
 第一類的用戶端取得伺服器的方法和屬性的相關資訊的方式是查詢 OLE 系統`IDispatch`機制。 雖然它是動態的用戶端，請使用適當`IDispatch`很難使用靜態用戶端，其中的物件被驅動必須已知道編譯時間。 Microsoft Foundation classes 靜態繫結的用戶端，提供[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)類別。  
  
 靜態繫結的用戶端會使用用戶端應用程式中的 proxy 類別，以靜態方式連結。 這個類別提供伺服器應用程式的屬性和作業的型別安全 c + + 封裝 （encapsulation 的）。  
  
 類別`COleDispatchDriver`提供自動化的用戶端的主要支援。 使用`Add New Item`對話方塊中，建立衍生自類別`COleDispatchDriver`。  
  
 然後，您會指定描述的屬性和伺服器應用程式的物件的函式的型別程式庫檔。 加入項目 對話方塊會讀取此檔案，並建立`COleDispatchDriver`-衍生的類別，與您的應用程式可以呼叫以類型安全的方式存取 c + + 中的伺服器應用程式的物件的成員函式。 其他功能繼承自`COleDispatchDriver`簡化呼叫適當的 Automation 伺服器的程序。  
  
### <a name="handling-events-in-automation-clients"></a>自動化用戶端中處理事件  
 如果您想要在您的 automation 用戶端中處理事件，您需要新增接收器介面。 MFC 提供精靈支援加入為 ActiveX 控制項的接收器介面，但支援其他 COM 伺服器。 如需如何新增接收器介面中所述的 COM 伺服器的來源介面的 MFC 用戶端資訊，請參閱 < 如何： 散發者端建立 MFC-Based COM 用戶端 (KB 181845) 中接收介面[ http://support.microsoft.com/default.aspxscid=kb; en-us-我們; 181845](http://support.microsoft.com/default.aspxscid=kb;en-us;181845)。  
  
## <a name="see-also"></a>另請參閱  
 [Automation 用戶端： 使用類型程式庫](../mfc/automation-clients-using-type-libraries.md)   
 [自動化](../mfc/automation.md)   
 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)

