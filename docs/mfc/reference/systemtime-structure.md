---
title: SYSTEMTIME 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- SYSTEMTIME structure [MFC]
ms.assetid: 9aaef4d6-de79-4fa1-8158-86b245ef5bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6882a4e169b7efa67bef02ab5abee1276384e52f
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334517"
---
# <a name="systemtime-structure"></a>SYSTEMTIME 結構

`SYSTEMTIME`結構代表日期和時間使用月、 日、 年、 週間日、 小時、 分鐘、 秒和毫秒的個別成員。

## <a name="syntax"></a>語法

```
typedef struct _SYSTEMTIME {
    WORD wYear;
    WORD wMonth;
    WORD wDayOfWeek;
    WORD wDay;
    WORD wHour;
    WORD wMinute;
    WORD wSecond;
    WORD wMilliseconds;
} SYSTEMTIME;
```

#### <a name="parameters"></a>參數

*wYear*<br/>
目前的年份。

*wMonth*<br/>
目前的月份;一月為 1。

*wDayOfWeek*<br/>
目前日期的星期幾;星期日是 0、 星期一是 1，依此類推。

*wDay*<br/>
目前月份天數。

*wHour*<br/>
目前的小時。

*wMinute*<br/>
目前的分鐘。

*wSecond*<br/>
目前的秒數。

*wMilliseconds*<br/>
目前的毫秒數。

## <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#39](../../mfc/codesnippet/cpp/systemtime-structure1_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** winbase.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CTime::CTime](../../atl-mfc-shared/reference/ctime-class.md#ctime)

