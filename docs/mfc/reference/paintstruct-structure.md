---
title: PAINTSTRUCT 結構
ms.date: 11/04/2016
f1_keywords:
- PAINTSTRUCT
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
ms.openlocfilehash: b5179a1bcba4a654ff235885ec2d0516e801fbb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677119"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT 結構

`PAINTSTRUCT`結構包含可用來繪製視窗工作區的資訊。

## <a name="syntax"></a>語法

```
typedef struct tagPAINTSTRUCT {
    HDC hdc;
    BOOL fErase;
    RECT rcPaint;
    BOOL fRestore;
    BOOL fIncUpdate;
    BYTE rgbReserved[16];
} PAINTSTRUCT;
```

#### <a name="parameters"></a>參數

*hdc*<br/>
識別要用來繪製的顯示內容。

*fErase*<br/>
指定是否需要重新繪製背景。 它不是 0，如果應用程式應該重新繪製背景。 應用程式會負責繪製背景，如果 Windows 視窗類別建立時沒有背景筆刷 (請參閱的說明`hbrBackground`隸屬[WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) Windows SDK 中的結構)。

*rcPaint*<br/>
指定的右上方，並降低要求在其中繪製的矩形的右角。

*fRestore*<br/>
保留的成員。 它是由 Windows 內部使用。

*fIncUpdate*<br/>
保留的成員。 它是由 Windows 內部使用。

*rgbReserved [16]*<br/>
保留的成員。 保留供內部使用 Windows 的記憶體區塊。

## <a name="requirements"></a>需求

**標頭：** winuser.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

