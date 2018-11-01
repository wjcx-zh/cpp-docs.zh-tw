---
title: FILETIME 結構
ms.date: 11/04/2016
f1_keywords:
- FILETIME
helpviewer_keywords:
- FILETIME structure [MFC]
ms.assetid: e09557e2-b6d7-4dd5-a5b9-6328bca88595
ms.openlocfilehash: f70792b83637018e707b6ee48d1b169f28d46d71
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514929"
---
# <a name="filetime-structure"></a>FILETIME 結構

`FILETIME`結構是 64 位元值，表示自 1601 年 1 月 1 日起的 100 奈秒間隔數。

## <a name="syntax"></a>語法

```
typedef struct _FILETIME {
    DWORD dwLowDateTime;   /* low 32 bits */
    DWORD dwHighDateTime;  /* high 32 bits */
} FILETIME, *PFILETIME, *LPFILETIME;
```

#### <a name="parameters"></a>參數

*dwLowDateTime*<br/>
指定的低 32 位元的檔案時間。

*dwHighDateTime*<br/>
指定高 32 位元的檔案時間。

## <a name="requirements"></a>需求

**標頭：** windef.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

