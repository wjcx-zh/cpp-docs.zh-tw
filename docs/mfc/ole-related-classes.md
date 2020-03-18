---
title: OLE 相關類別
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: dfcc07b3fbd0c5badce8e397f4d52bc7d8d3028c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447600"
---
# <a name="ole-related-classes"></a>OLE 相關類別

這些類別提供數種不同服務，範圍從例外狀況到檔案輸入和輸出。

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
用來在其他容器有需求時建立項目。 這個類別可做為類型較為特定的 Factory 的基底類別，包括 `COleTemplateServer`。

[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)<br/>
用來管理與 OLE 輕量型遠端程序呼叫 (LRPC) 的並行。

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
使用 COM `IStream` 介面提供複合檔案的 `CFile` 存取權。 這個類別 (衍生自 `CFile`) 可讓 MFC 序列化使用 OLE 結構化儲存體。

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
用來允許移動就地項目、調整其大小和重新定位。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)
