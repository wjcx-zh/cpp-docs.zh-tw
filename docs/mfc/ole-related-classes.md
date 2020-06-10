---
title: OLE 相關類別
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 6f6db6ce133b440a5ed86e7c1642396888744540
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621025"
---
# <a name="ole-related-classes"></a>OLE 相關類別

這些類別提供數種不同服務，範圍從例外狀況到檔案輸入和輸出。

[COleObjectFactory](reference/coleobjectfactory-class.md)<br/>
用來在其他容器有需求時建立項目。 這個類別可做為類型較為特定的 Factory 的基底類別，包括 `COleTemplateServer`。

[COleMessageFilter](reference/colemessagefilter-class.md)<br/>
用來管理與 OLE 輕量型遠端程序呼叫 (LRPC) 的並行。

[COleStreamFile](reference/colestreamfile-class.md)<br/>
使用 COM `IStream` 介面提供複合檔案的 `CFile` 存取權。 這個類別 (衍生自 `CFile`) 可讓 MFC 序列化使用 OLE 結構化儲存體。

[CRectTracker](reference/crecttracker-class.md)<br/>
用來允許移動就地項目、調整其大小和重新定位。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)
