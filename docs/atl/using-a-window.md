---
title: 使用視窗 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
ms.openlocfilehash: 7446196e9eec4b9d9236d4ab55afd9fcf859254b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568648"
---
# <a name="using-a-window"></a>使用視窗

類別[CWindow](../atl/reference/cwindow-class.md)可讓您使用的視窗。 一旦您將附加到視窗`CWindow`物件，您就可以呼叫`CWindow`管理視窗的方法。 `CWindow` 也包含 HWND 運算子以轉換`CWindow`HWND 的物件。 因此，您可以傳遞`CWindow`任何需要的視窗控制代碼的函式的物件。 您可以輕鬆地混合`CWindow`方法呼叫和 Win32 函式呼叫，而不需要建立任何暫存物件。

因為`CWindow`只有兩個資料成員 （視窗控制代碼和預設大小），它不會造成您的程式碼的負荷。 此外，許多`CWindow`方法只會包裝對應的 Win32 API 函式。 使用`CWindow`，HWND 成員會自動傳遞給 Win32 函式。

除了使用`CWindow`直接，您也可以衍生自以將資料或程式碼新增到您的類別。 ATL 本身衍生中的三個類別`CWindow`: [CWindowImpl](../atl/implementing-a-window.md)， [CDialogImpl](../atl/implementing-a-dialog-box.md)，和[CContainedWindowT](../atl/using-contained-windows.md)。

## <a name="see-also"></a>另請參閱

[視窗類別](../atl/atl-window-classes.md)

