---
title: 將通用控制項做為子視窗使用
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], using as child windows
- windows [MFC], common controls as
- child windows [MFC], common controls as
- common controls [MFC], child windows
- Windows common controls [MFC], child windows
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
ms.openlocfilehash: 690b48cf50e95265aaf5bdd454e2881b8f5fab3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655126"
---
# <a name="using-a-common-control-as-a-child-window"></a>將通用控制項做為子視窗使用

所有 Windows 通用控制項都可以做為其他視窗中的子視窗。 下列程序描述如何動態建立通用控制項並使用該控制項。

### <a name="to-use-a-common-control-as-a-child-window"></a>使用通用控制項做為子視窗

1. 在相關的類別或處理常式中定義控制項。

1. 使用控制項的覆寫[cwnd:: Create](../mfc/reference/cwnd-class.md#create)方法用來建立 Windows 控制項。

1. 在建立控制項後 (如果您子類別化控制項，則在 `OnCreate` 處理常式之前)，您可以使用其成員函式來操作控制項。 請參閱 < 個別控制項的說明[控制項](../mfc/controls-mfc.md)如方法的詳細資訊。

1. 當您使用控制項時，請使用[cwnd:: Destroywindow](../mfc/reference/cwnd-class.md#destroywindow)終結控制項。

## <a name="see-also"></a>另請參閱

[建立及使用控制項](../mfc/making-and-using-controls.md)<br/>
[控制項](../mfc/controls-mfc.md)

