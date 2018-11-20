---
title: 管理 MDI 子視窗
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: d4b6ccf8a75cc7679f78fba48314073bc53b66a5
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176792"
---
# <a name="managing-mdi-child-windows"></a>管理 MDI 子視窗

MDI 主框架視窗 （其中每個應用程式） 包含稱為 MDICLIENT 視窗的特殊子視窗。 MDICLIENT 視窗管理工作區的主框架視窗中，而其本身具有子視窗: 文件視窗中，衍生自`CMDIChildWnd`。 由於文件視窗本身是框架視窗 (MDI 子視窗)，因此也可以有自己的子視窗。 在所有這些情況中，父視窗會管理其子視窗，並將一些命令轉送給它們。

在 MDI 框架視窗中，框架視窗會管理 MDICLIENT 視窗中，與控制列一起重新置放。 MDICLIENT 視窗中，會管理所有 MDI 子框架視窗。 下圖顯示 MDI 框架視窗、 其 MDICLIENT 視窗和其子文件框架視窗之間的關聯性。

![MDI 框架視窗中的子視窗](../mfc/media/vc37gb1.gif "MDI 框架視窗中的子視窗") <br/>
MDI 框架視窗和子視窗

如果有的話，MDI 框架視窗也會與目前 MDI 子視窗一起運作。 在嘗試自行處理之前，MDI 框架視窗會委派命令訊息至 MDI 子視窗。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立文件框架視窗](../mfc/creating-document-frame-windows.md)

- [框架視窗樣式](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>另請參閱

[使用框架視窗](../mfc/using-frame-windows.md)

