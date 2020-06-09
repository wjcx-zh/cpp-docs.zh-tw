---
title: 初始化文件和檢視
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 0e970d6e8a166283f82575b309cf023f48899403
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626358"
---
# <a name="initializing-documents-and-views"></a>初始化文件和檢視

文件是以兩種不同的方式建立，因此您的文件類別必須支援這兩種方式。 首先，使用者可以使用 [開新檔案] 命令建立新的空白文件。 在這種情況下，請在[CDocument](reference/cdocument-class.md)類別的[OnNewDocument](reference/cdocument-class.md#onnewdocument)成員函式的覆寫中初始化檔。 其次，使用者可以使用 [檔案] 功能表的 [開啟] 命令建立從某個檔案讀取內容的新文件。 在此情況下，請在您的類別之[OnOpenDocument](reference/cdocument-class.md#onopendocument)成員函式的覆寫中初始化檔 `CDocument` 。 如果兩種初始化方式相同，您可以從兩個覆寫中呼叫一個共同的成員函式，或者 `OnOpenDocument` 可以呼叫 `OnNewDocument` 以初始化全新的文件後再完成開啟作業。

在建立其文件後會建立檢視。 初始化檢視的最佳時機是在架構完成建立文件、框架視窗與檢視之後。 您可以藉由覆寫[CView](reference/cview-class.md)的[OnInitialUpdate](reference/cview-class.md#oninitialupdate)成員函式來初始化您的 view。 如果您需要在每次檔變更時重新初始化或調整任何專案，您可以覆寫[OnUpdate](reference/cview-class.md#onupdate)。

## <a name="see-also"></a>另請參閱

[初始化及清除文件和檢視](initializing-and-cleaning-up-documents-and-views.md)
