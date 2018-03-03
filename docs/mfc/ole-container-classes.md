---
title: "OLE 容器類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df809971ecf8bdd8700217cf6a1965e2973de754
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ole-container-classes"></a>OLE 容器類別
容器應用程式會使用這些類別。 同時`COleLinkingDoc`和`COleDocument`管理集合的`COleClientItem`物件。 而不是衍生您的文件類別，從**CDocument**，您會從它衍生`COleLinkingDoc`或`COleDocument`，視您是否要支援的連結文件中內嵌的物件。  
  
 使用`COleClientItem`物件以代表從另一個文件中內嵌或連結至另一個文件的文件中的每個 OLE 項目。  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 支援使用中文件內含項目。  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 用於複合文件的實作，以及基本的容器支援。 做為容器類別，衍生自`CDocItem`。 這個類別可用來當作基底類別的文件容器中，是基底類別`COleServerDoc`。  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 類別衍生自`COleDocument`所提供的基礎結構連結。 您應該為容器應用程式而不是從這個類別衍生的文件類別`COleDocument`如果您想要支援內嵌物件連結。  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 維護 rich edit 控制項中的 OLE 用戶端項目的清單。 搭配[CRichEditView](../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 抽象基底類別的`COleClientItem`和`COleServerItem`。 物件的類別衍生自`CDocItem`代表文件的部分。  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 用戶端項目類別，表示要內嵌或連結 OLE 項目之連接的用戶端的側邊。 從這個類別衍生您的用戶端項目。  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 提供 OLE 項目儲存在 rich edit 控制項搭配使用時的用戶端存取`CRichEditView`和`CRichEditDoc`。  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

