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
ms.openlocfilehash: 6e8e3d0aa51eeea112597485a9221dcba4feda87
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618366"
---
# <a name="managing-mdi-child-windows"></a>管理 MDI 子視窗

MDI 主框架視窗 (每應用程式一個視窗) 包含呼叫 MDICLIENT 視窗的特殊子視窗。 [MDICLIENT] 視窗會管理主框架視窗的工作區，而且本身會有子視窗：文件視窗，衍生自 `CMDIChildWnd` 。 由於文件視窗本身是框架視窗 (MDI 子視窗)，因此也可以有自己的子視窗。 在所有這些情況中，父視窗會管理其子視窗，並將一些命令轉送給它們。

在 MDI 框架視窗中，框架視窗會管理 MDICLIENT 視窗，與控制列一起重新置放。 然後 MDICLIENT 視窗會管理所有 MDI 子框架視窗。 下圖顯示 MDI 框架視窗、其 MDICLIENT 視窗及其子文件框架視窗之間的關聯性。

![MDI 框架視窗中的子視窗](../mfc/media/vc37gb1.gif "MDI 框架視窗中的子視窗") <br/>
MDI 框架視窗和子視窗

如果有的話，MDI 框架視窗也會與目前 MDI 子視窗一起運作。 在嘗試自行處理之前，MDI 框架視窗會委派命令訊息至 MDI 子視窗。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [建立檔框架視窗](creating-document-frame-windows.md)

- [框架視窗樣式](frame-window-styles-cpp.md)

## <a name="see-also"></a>另請參閱

[使用框架視窗](using-frame-windows.md)
