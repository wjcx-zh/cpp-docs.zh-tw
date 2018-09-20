---
title: WINDOWPLACEMENT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b163d93de22d313d72ca5dbfd384788077ae1b01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447269"
---
# <a name="windowplacement-structure"></a>WINDOWPLACEMENT 結構

`WINDOWPLACEMENT`結構包含在螢幕上視窗的位置之詳細資訊。

## <a name="syntax"></a>語法

```
typedef struct tagWINDOWPLACEMENT {     /* wndpl */
    UINT length;
    UINT flags;
    UINT showCmd;
    POINT ptMinPosition;
    POINT ptMaxPosition;
    RECT rcNormalPosition;
} WINDOWPLACEMENT;
```

#### <a name="parameters"></a>參數

*length*<br/>
指定長度，以位元組為單位的結構。

*flags*<br/>
指定旗標所控制的最小化的視窗和方法還原視窗的位置。 這個成員可以是其中一個或多個下列旗標：

- WPF_SETMINPOSITION 指定，您可以指定 x-和 y-位置的最小化視窗。 這個旗標必須是指定是否座標會設定在`ptMinPosition`成員。

- WPF_RESTORETOMAXIMIZED 指定，還原將會最大化視窗，不論是否它有經過最大化之前的最小化。 這項設定是有效的僅還原視窗在下一次。 它不會變更預設還原行為。 此旗標是有效的只有在指定 SW_SHOWMINIMIZED 值時，才`showCmd`成員。

*showCmd*<br/>
指定目前的顯示狀態的視窗。 這個成員可以是下列值之一：

- SW_HIDE 隱藏視窗，並將啟用傳遞至另一個視窗。

- SW_MINIMIZE 指定的視窗最小化，並啟動系統的清單中的最上層視窗。

- SW_RESTORE 啟動並顯示視窗。 如果視窗是最小化或最大化，則 Windows 會將它還原至其原始大小和位置 （與 SW_SHOWNORMAL 相同）。

- SW_SHOW 啟動視窗並將它顯示在其目前的大小和位置。

- Sw_showmaximized 其中一個啟動的視窗，並顯示最大化視窗。

- SW_SHOWMINIMIZED 啟動視窗並將它顯示為圖示。

- SW_SHOWMINNOACTIVE 圖示形式顯示的視窗。 目前使用中視窗保持作用中。

- SW_SHOWNA 顯示的視窗在其目前的狀態。 目前使用中視窗保持作用中。

- SW_SHOWNOACTIVATE 顯示的視窗中的最新的大小和位置。 目前使用中視窗保持作用中。

- SW_SHOWNORMAL 啟動並顯示視窗。 如果視窗是最小化或最大化，則 Windows 會將它還原至其原始大小和位置 （與 SW_RESTORE 相同）。

*ptMinPosition*<br/>
當視窗最小化時，請指定視窗的左上角的位置。

*ptMaxPosition*<br/>
當視窗最大化時，請指定視窗的左上角的位置。

*rcNormalPosition*<br/>
當視窗在一般 （還原） 的位置時，請指定視窗的座標。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

