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
ms.openlocfilehash: 70740922ec7f2030d14eebee72144a373550aacc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768883"
---
# <a name="printing-and-print-preview"></a>列印和預覽列印

MFC 類別透過您的程式文件支援列印和預覽列印[CView](../mfc/reference/cview-class.md)。 基本列印和預覽列印，只是覆寫檢視類別的[OnDraw](../mfc/reference/cview-class.md#ondraw)成員函式，您必須做的動作罷了。 該函式可以繪製到螢幕，實際的印表機的印表機裝置內容的檢視，或模擬您在螢幕上的印表機裝置內容。

您也可以加入程式碼來管理多頁文件列印和預覽，編頁列印的文件，並將頁首和頁尾加入至它們。

此系列文章說明如何實作列印在 Microsoft Foundation Class 程式庫 (MFC)，以及如何善用列印已內建於 framework 的架構。 文章也會說明如何 MFC 支援的預覽列印功能的簡單實作，以及如何使用及修改該功能。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [列印](../mfc/printing.md)

- [預覽列印架構](../mfc/print-preview-architecture.md)

- [範例](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)
