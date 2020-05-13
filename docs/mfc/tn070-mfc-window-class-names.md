---
title: TN070：MFC 視窗類別名稱
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: ad43f5af5d2e90cb5fc2bc90f0909c2b495b4a4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373490"
---
# <a name="tn070-mfc-window-class-names"></a>TN070：MFC 視窗類別名稱

> [!NOTE]
> 下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

MFC 視窗會使用動態建立的類別名稱反映視窗的功能。 MFC 會動態為應用程式所產生的框架視窗、檢視和快顯視窗，產生類別名稱。 不確定視窗的類別時，MFC 應用程式所產生的對話方塊和控制項會使用 Windows 所提供的名稱。

您可以通過註冊自己的視窗類並在[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)中使用它來替換動態提供的類名稱。 MFC 提供的類別名稱採用下列兩種格式之一：

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

替換字元的`%x`十六進位數位是從[WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw)結構的數據中填充的。 MFC 使用此技術,以便需要相同**WNDCLASS**結構的多個C++類可以共用相同的註冊視窗類。 與最簡單的 Win32 應用程式不同,MFC 應用程式只有一個**WNDPROC,** 因此您可以輕鬆地共用**WNDCLASS**結構以節省時間和記憶體。 可取代以上所顯示 `%x` 字元的值如下：

- **WNDCLASS.hInstance**

- **WNDCLASS.style**

- **WNDCLASS.hCursor**

- **WNDCLASS.hbrBackground**

- **WNDCLASS.hIcon**

`Afx:%x:%x`當**hCursor**hCursor、hbrBackground**hbrBackground**與**hIcon**都是**NULL**時,將使用第一個窗體 ( ) 。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)<br/>
[TN020：ID 命名和編號慣例](../mfc/tn020-id-naming-and-numbering-conventions.md)
