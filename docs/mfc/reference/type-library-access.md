---
title: 類型程式庫存取
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 1794e16489ab48d919bbd4116588fba4b74b88d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372879"
---
# <a name="type-library-access"></a>類型程式庫存取

類型程式庫會將 OLE 控制項的介面公開給其他 OLE 感知應用程式。 如果有一個或多個介面要公開，則每個 OLE 控制項都必須有類型程式庫。

下列巨集可以讓 OLE 控制項提供對其類型程式庫的存取能力：

### <a name="type-library-access"></a>類型程式庫存取

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|宣告 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別宣告中使用)。|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|實作 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別實作中使用)。|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

聲明控件類`GetTypeLib`的成員函數。

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
與類型庫相關的控制項類的名稱。

### <a name="remarks"></a>備註

在控件類標頭檔中使用此宏。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

實現控件的成員`GetTypeLib`函數。

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>參數

*class_name*<br/>
與類型庫相關的控制項類的名稱。

*tlid*<br/>
類型庫的 ID 號。

*wVerMajor*<br/>
類型庫主要版本號。

*wVerMinor*<br/>
類型庫次要版本號。

### <a name="remarks"></a>備註

對於使用DECLARE_OLETYPELIB宏的任何控制類,此宏必須出現在實現檔中。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
