---
title: MFC 應用程式精靈所建立的文件和檢視類別
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: 766fe4efb37c199c5babb75ce2cb08ebf676cca6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616044"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>MFC 應用程式精靈所建立的文件和檢視類別

「MFC 應用程式精靈」藉由建立基本架構文件和檢視類別，讓您在程式開發上能夠捷足先登。 接著，您可以將[命令和訊息對應至這些類別](reference/mapping-messages-to-functions.md)，並使用 Visual C++ 的原始程式碼編輯器來撰寫其成員函式。

MFC 應用程式精靈所建立的檔類別是衍生自類別[CDocument](reference/cdocument-class.md)。 View 類別衍生自[CView](reference/cview-class.md)。 應用程式精靈給予這些類別的名稱以及包含這些的檔案，是以您在 [應用程式精靈] 對話方塊中提供的專案名稱為根據。 在 [應用程式精靈] 中，您可以使用 [產生的類別] 頁面修改預設名稱。

部分應用程式可能需要多個文件類別、檢視類別或框架視窗類別。 如需詳細資訊，請參閱[多個檔案類型、視圖和框架視窗](multiple-document-types-views-and-frame-windows.md)。

## <a name="see-also"></a>另請參閱

[檔/視圖架構](document-view-architecture.md)
