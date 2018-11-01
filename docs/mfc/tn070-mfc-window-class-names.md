---
title: TN070：MFC 視窗類別名稱
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.classes
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: d59dc052cc253c8d036de0559018065e4ba7457d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533610"
---
# <a name="tn070-mfc-window-class-names"></a>TN070：MFC 視窗類別名稱

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

MFC 視窗會使用動態建立的類別名稱反映視窗的功能。 MFC 會動態為應用程式所產生的框架視窗、檢視和快顯視窗，產生類別名稱。 不確定視窗的類別時，MFC 應用程式所產生的對話方塊和控制項會使用 Windows 所提供的名稱。

您可以註冊自己的視窗類別並覆寫中使用它來取代動態提供的類別名稱[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)。 MFC 提供的類別名稱採用下列兩種格式之一：

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

取代的十六進位數字`%x`字元會從資料填入[WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)結構。 MFC 使用這項技術，讓多個需要相同的 c + + 類別**WNDCLASS**結構可以共用相同的已註冊的視窗類別。 不同於大部分簡易的 Win32 應用程式，MFC 應用程式只能有一個**WNDPROC**，因此您可以輕鬆地共用**WNDCLASS**結構，以節省時間和記憶體。 可取代以上所顯示 `%x` 字元的值如下：

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

第一種形式 (`Afx:%x:%x`) 時使用**hCursor**， **hbrBackground**，和**hIcon**都**NULL**。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)<br/>
[TN020：識別碼命名和編號慣例](../mfc/tn020-id-naming-and-numbering-conventions.md)

