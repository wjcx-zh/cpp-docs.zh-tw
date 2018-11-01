---
title: NCCALCSIZE_PARAMS 結構
ms.date: 11/04/2016
f1_keywords:
- NCCALCSIZE_PARAMS
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
ms.openlocfilehash: 3dbe1fcdb941a94876dd95a0eed86d6f4a3e15c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443767"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS 結構

`NCCALCSIZE_PARAMS`結構包含應用程式可以使用在處理 WM_NCCALCSIZE 訊息時，若要計算的大小、 位置和有效的用戶端區域內容的視窗的資訊。

## <a name="syntax"></a>語法

```
typedef struct tagNCCALCSIZE_PARAMS {
    RECT rgrc[3];
    PWINDOWPOS lppos;
} NCCALCSIZE_PARAMS;
```

#### <a name="parameters"></a>參數

*rgrc*<br/>
指定矩形的陣列。 第一個包含新的座標移動或調整大小的視窗。 移動或調整大小之前，第二個包含視窗的座標。 移動或調整大小之前，第三個包含視窗的工作區座標。 如果視窗是子視窗，座標是相對於父視窗工作區。 如果視窗是最上層視窗，座標是相對於畫面。

*lppos*<br/>
指向[WINDOWPOS](../../mfc/reference/windowpos-structure1.md)結構，其中包含造成移動或調整大小視窗的作業中指定的大小和位置的值。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

