---
title: OLE Automation 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea35e51296b2fc528657c4dd9f9b9b76b84aae83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391510"
---
# <a name="ole-automation-classes"></a>OLE Automation 類別

這些類別支援 automation 用戶端 （控制其他應用程式的應用程式）。 Automation 伺服程式 （可以受到其他應用程式的應用程式） 支援透過[分派對應](../mfc/reference/dispatch-maps.md)。

[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)<br/>
用來從您的自動化用戶端呼叫 automation 伺服程式。 當加入類別，這個類別用來建立 automation 伺服程式，提供型別程式庫的型別安全類別。

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
OLE automation 期間所產生的錯誤例外狀況。 Automation 例外狀況由 Automation 伺服程式擲回，並由 Automation 用戶端攔截。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

