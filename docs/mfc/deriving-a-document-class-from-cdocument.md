---
title: 從 CDocument 衍生文件類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b45dadbc062bbba61cdcb4c883f91943b1b18ba8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429821"
---
# <a name="deriving-a-document-class-from-cdocument"></a>從 CDocument 衍生文件類別

文件包含並管理您的應用程式資料。 若要使用的 MFC 應用程式精靈提供的文件類別，您必須執行下列作業：

- 自`CDocument`每種類型的文件。

- 加入成員變數以儲存每個文件的資料。

- 覆寫`CDocument`的`Serialize`文件類別中的成員函式。 `Serialize` 寫入和讀取文件的資料磁碟。

## <a name="other-document-functions-often-overridden"></a>通常被覆寫的其他文件函式

您也可以覆寫其他`CDocument`成員函式。 特別是，您通常需要覆寫[OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument)並[OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument)初始化文件的資料成員和[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)終結以動態方式配置資料。 如需可覆寫成員的資訊，請參閱類別[CDocument](../mfc/reference/cdocument-class.md)中*MFC 參考 》*。

## <a name="see-also"></a>另請參閱

[使用文件](../mfc/using-documents.md)

