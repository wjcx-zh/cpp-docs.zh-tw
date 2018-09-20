---
title: 文件和檢視類別建立 MFC 應用程式精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb1a1fc6c35bfb9589e827d798cb112640fa9b2f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417614"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>MFC 應用程式精靈所建立的文件和檢視類別

「MFC 應用程式精靈」藉由建立基本架構文件和檢視類別，讓您在程式開發上能夠捷足先登。 您可以接著[將命令和訊息對應到這些類別](../mfc/reference/mapping-messages-to-functions.md)並用 Visual c + + 原始程式碼編輯器來撰寫其成員函式。

MFC 應用程式精靈所建立的文件類別衍生自類別[CDocument](../mfc/reference/cdocument-class.md)。 檢視類別衍生自[CView](../mfc/reference/cview-class.md)。 應用程式精靈給予這些類別的名稱以及包含這些的檔案，是以您在 [應用程式精靈] 對話方塊中提供的專案名稱為根據。 在 [應用程式精靈] 中，您可以使用 [產生的類別] 頁面修改預設名稱。

部分應用程式可能需要多個文件類別、檢視類別或框架視窗類別。 如需詳細資訊，請參閱 <<c0> [ 多個文件類型、 檢視和框架 Windows](../mfc/multiple-document-types-views-and-frame-windows.md)。

## <a name="see-also"></a>另請參閱

[文件/檢視架構](../mfc/document-view-architecture.md)

