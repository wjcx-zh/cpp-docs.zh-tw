---
title: 從 CDocument 衍生文件類別
ms.date: 11/04/2016
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
ms.openlocfilehash: 399230446977636cc8769efe32b8f86fad466b83
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616109"
---
# <a name="deriving-a-document-class-from-cdocument"></a>從 CDocument 衍生文件類別

檔包含和管理您的應用程式資料。 若要使用 MFC 應用程式精靈提供的檔類別，您必須執行下列動作：

- `CDocument`針對每一種檔案類型從衍生類別。

- 新增成員變數以儲存每份檔的資料。

- `CDocument` `Serialize` 在您的檔類別中覆寫的成員函式。 `Serialize`從磁片寫入和讀取檔的資料。

## <a name="other-document-functions-often-overridden"></a>其他檔功能通常會遭到覆寫

您可能也會想要覆寫其他成員函式 `CDocument` 。 特別的是，您通常需要覆寫[OnNewDocument](reference/cdocument-class.md#onnewdocument)和[OnOpenDocument](reference/cdocument-class.md#onopendocument) ，將檔的資料成員和[DeleteContents](reference/cdocument-class.md#deletecontents)初始化，以終結動態配置的資料。 如需可覆寫成員的詳細資訊，請參閱*MFC 參考*中的類別[CDocument](reference/cdocument-class.md) 。

## <a name="see-also"></a>另請參閱

[使用文件](using-documents.md)
