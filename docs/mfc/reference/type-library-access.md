---
title: 類型程式庫存取
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 55d6a56f566416bb25f3ee3ae508c86f17f0df99
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840449"
---
# <a name="type-library-access"></a>類型程式庫存取

類型程式庫會將 OLE 控制項的介面公開給其他 OLE 感知應用程式。 如果有一個或多個介面要公開，則每個 OLE 控制項都必須有類型程式庫。

下列巨集可以讓 OLE 控制項提供對其類型程式庫的存取能力：

### <a name="type-library-access"></a>類型程式庫存取

|名稱|描述|
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|宣告 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別宣告中使用)。|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|實作 OLE 控制項的 `GetTypeLib` 成員函式 (必須在類別實作中使用)。|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a> DECLARE_OLETYPELIB

宣告 `GetTypeLib` 控制項類別的成員函式。

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
與類型程式庫相關的控制項類別名稱。

### <a name="remarks"></a>備註

在控制項類別標頭檔中使用此宏。

### <a name="requirements"></a>規格需求

**標頭：** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a> IMPLEMENT_OLETYPELIB

實行控制項的成員函式 `GetTypeLib` 。

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>參數

*class_name*<br/>
與類型程式庫相關的控制項類別名稱。

*tlid*<br/>
類型程式庫的識別碼。

*wVerMajor*<br/>
類型程式庫的主要版本號碼。

*wVerMinor*<br/>
類型程式庫次要版本號碼。

### <a name="remarks"></a>備註

此宏必須出現在使用 DECLARE_OLETYPELIB 宏之任何控制項類別的執行檔中。

### <a name="requirements"></a>規格需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
