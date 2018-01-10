---
title: "伺服器： 實作伺服器文件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c4b8618e4951ac499d504cc68b0552ea45eed03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="servers-implementing-server-documents"></a>伺服器：實作伺服器文件
本文說明如果您未指定應用程式精靈中的 OLE 伺服器選項，成功實作伺服器文件時，必須採取的步驟。  
  
#### <a name="to-define-a-server-document-class"></a>若要定義伺服器文件類別  
  
1.  衍生您的文件類別，從`COleServerDoc`而不是**CDocument**。  
  
2.  建立伺服器項目類別衍生自`COleServerItem`。  
  
3.  實作`OnGetEmbeddedItem`伺服器文件類別的成員函式。  
  
     `OnGetEmbeddedItem`容器應用程式的使用者建立或編輯內嵌項目時呼叫。 它應該會傳回代表整個文件的項目。 這應該是物件的程式`COleServerItem`-衍生的類別。  
  
4.  覆寫`Serialize`序列化文件內容的成員函式。 您不需要序列化的伺服器項目清單，除非您正在使用它們來代表文件中的原生資料。 如需詳細資訊，請參閱*實作伺服器項目*本文[伺服器： 伺服器項目](../mfc/servers-server-items.md)。  
  
 建立伺服器文件時，架構會自動註冊文件與 OLE 系統 Dll。 這可讓 Dll 識別伺服器文件。  
  
 如需詳細資訊，請參閱[COleServerItem](../mfc/reference/coleserveritem-class.md)和[COleServerDoc](../mfc/reference/coleserverdoc-class.md)中*類別庫參考*。  
  
## <a name="see-also"></a>請參閱  
 [伺服器](../mfc/servers.md)   
 [伺服器： 伺服器項目](../mfc/servers-server-items.md)   
 [伺服器： 實作伺服器](../mfc/servers-implementing-a-server.md)   
 [伺服器：實作就地編輯框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)

