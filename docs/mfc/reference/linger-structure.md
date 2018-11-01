---
title: LINGER 結構
ms.date: 11/04/2016
f1_keywords:
- LINGER
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
ms.openlocfilehash: 78f1a5ce993373ea9e477262f0779515c52dbd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495308"
---
# <a name="linger-structure"></a>LINGER 結構

`LINGER`結構用於操作的 SO_LINGER 和 SO_DONTLINGER 選項`CAsyncSocket::GetSockOpt`。

## <a name="syntax"></a>語法

```
struct linger {
    u_short l_onoff;            // option on/off
    u_short l_linger;           // linger time
};
```

## <a name="remarks"></a>備註

將 SO_DONTLINGER 選項可防止封鎖成員函式`Close`等候要傳送之未傳送資料。 設定此選項相當於設定與 SO_LINGER`l_onoff`設為 0。

## <a name="requirements"></a>需求

**標頭：** winsock2.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)<br/>
[CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

