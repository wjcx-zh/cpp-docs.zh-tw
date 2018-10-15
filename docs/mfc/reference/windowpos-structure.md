---
title: WINDOWPOS 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure [MFC]
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36e640187a87f3776a67a072e2fe77c141ed23f0
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334518"
---
# <a name="windowpos-structure"></a>WINDOWPOS 結構

`WINDOWPOS`結構包含大小和視窗位置資訊。

## <a name="syntax"></a>語法

```
typedef struct tagWINDOWPOS { /* wp */
    HWND hwnd;
    HWND hwndInsertAfter;
    int x;
    int y;
    int cx;
    int cy;
    UINT flags;
} WINDOWPOS;
```

#### <a name="parameters"></a>參數

*hwnd*<br/>
識別視窗。

*hwndInsertAfter*<br/>
識別此視窗會放置其後的視窗。

*x*<br/>
指定視窗的左邊緣的位置。

*y*<br/>
指定視窗的右邊緣的位置。

*cx*<br/>
指定視窗的寬度，單位為像素。

*cy*<br/>
指定視窗的高度，單位為像素。

*flags*<br/>
指定視窗定位的選項。 這個成員可以是下列值之一：

- SWP_DRAWFRAME 繪製視窗周圍框架 （定義於視窗類別描述）。 視窗收到 WM_NCCALCSIZE 訊息。

- SWP_FRAMECHANGED 傳送 WM_NCCALCSIZE 訊息至 視窗中，即使未變更視窗的大小。 如果未指定此旗標，則只在視窗的大小變更時，才傳送 WM_NCCALCSIZE。

- SWP_HIDEWINDOW 隱藏視窗。

- SWP_NOACTIVATE 不會啟動視窗。

- SWP_NOCOPYBITS 捨棄工作區的整個內容。 如果未指定此旗標，工作區的有效內容就會儲存，並複製回工作區之後的視窗大小或重新調整位置。

- SWP_NOMOVE 會保留目前的位置 (會忽略`x`和`y`成員)。

- SWP_NOOWNERZORDER 不會變更疊置順序中的主控視窗的位置。

- SWP_NOSIZE 會保留目前的大小 (會忽略`cx`和`cy`成員)。

- SWP_NOREDRAW 不重繪其變更。

- SWP_NOREPOSITION SWP_NOOWNERZORDER 與相同。

- SWP_NOSENDCHANGING 會防止視窗接收 WM_WINDOWPOSCHANGING 訊息。

- SWP_NOZORDER 會保留目前的訂購 (會忽略`hwndInsertAfter`成員)。

- SWP_SHOWWINDOW 顯示視窗。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

