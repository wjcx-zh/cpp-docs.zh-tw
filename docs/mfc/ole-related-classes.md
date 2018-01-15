---
title: "OLE 相關類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4cb40e237eb6197dfe7e0cf944f12d25ca0e28e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ole-related-classes"></a>OLE 相關類別
這些類別提供數種不同服務，範圍從例外狀況到檔案輸入和輸出。  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 用來在其他容器有需求時建立項目。 這個類別可做為類型較為特定的 Factory 的基底類別，包括 `COleTemplateServer`。  
  
 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 用來管理與 OLE 輕量型遠端程序呼叫 (LRPC) 的並行。  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 使用 COM `IStream` 介面提供複合檔案的 `CFile` 存取權。 這個類別 (衍生自 `CFile`) 可讓 MFC 序列化使用 OLE 結構化儲存體。  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 用來允許移動就地項目、調整其大小和重新定位。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

