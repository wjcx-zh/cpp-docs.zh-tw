---
title: DHtmlUrlEventMapEntry 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DHtmlUrlEventMapEntry
dev_langs:
- C++
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbac4b372f06f288eede8c578372d45334a5d707
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427520"
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

