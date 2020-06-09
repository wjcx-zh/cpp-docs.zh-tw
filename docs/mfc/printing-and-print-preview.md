---
title: 列印和預覽列印
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 26ced8172a36d34883d6b65997bb3a81fdc3c319
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625269"
---
# <a name="printing-and-print-preview"></a>列印和預覽列印

MFC 支援透過類別[CView](reference/cview-class.md)進行程式檔的列印和預覽列印。 針對基本列印和預覽列印，只需要覆寫您的 view 類別的[OnDraw](reference/cview-class.md#ondraw)成員函式，您仍然必須這麼做。 該函式可以繪製到螢幕上的視圖、實際印表機的印表機裝置內容，或在螢幕上模擬印表機的裝置內容。

您也可以加入程式碼來管理多頁檔列印和預覽、將列印的檔分頁，以及在其中加入頁首和頁尾。

這一系列的文章說明如何在 MFC 程式庫（MFC）中執行列印，以及如何利用已經內建在架構中的列印架構。 本文也會說明 MFC 如何支援輕鬆地執行預覽列印功能，以及如何使用和修改該功能。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [列印](printing.md)

- [預覽列印架構](print-preview-architecture.md)

- [範例](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[使用者介面元素](user-interface-elements-mfc.md)
