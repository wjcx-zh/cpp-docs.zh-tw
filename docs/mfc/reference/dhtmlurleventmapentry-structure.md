---
title: DHtmlUrlEventMapEntry 結構
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: 0a1dc86080c094a7ac89940cd43a8edac973e10c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431625"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry 結構

`DHtmlUrlEventMapEntry`結構提供多 URL 事件對應支援。

## <a name="syntax"></a>語法

```
struct DHtmlUrlEventMapEntry
{
LPCTSTR szUrl;
const DHtmlEventMapEntry *pEventMap;
};
```

#### <a name="parameters"></a>參數

*szUrl*<br/>
URL。

*pEventMap*<br/>
事件對應 URL 相關聯。

## <a name="requirements"></a>需求

**標頭：** afxdhtml.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

