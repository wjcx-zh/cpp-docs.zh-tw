---
title: 類型程式庫存取
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420747"
---
# <a name="type-library-access"></a>類型程式庫存取

類型程式庫會將 OLE 控制項的介面公開給其他 OLE 感知應用程式。 如果有一個或多個介面要公開，則每個 OLE 控制項都必須有類型程式庫。

下列巨集可以讓 OLE 控制項提供對其類型程式庫的存取能力：

### <a name="type-library-access"></a>類型程式庫存取

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|宣告 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別宣告中使用)。|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|實作 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別實作中使用)。|

##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

宣告控制項類別的 `GetTypeLib` 成員函式。

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
與類型程式庫相關的控制項類別名稱。

### <a name="remarks"></a>備註

在控制項類別標頭檔中使用這個宏。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

實作用控制項的 `GetTypeLib` 成員函式。

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>參數

*class_name*<br/>
與類型程式庫相關的控制項類別名稱。

*tlid*<br/>
類型程式庫的 ID 編號。

*wVerMajor*<br/>
類型程式庫的主要版本號碼。

*wVerMinor*<br/>
類型程式庫次要版本號碼。

### <a name="remarks"></a>備註

這個宏必須出現在任何使用 DECLARE_OLETYPELIB 宏之控制項類別的執行檔中。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)
