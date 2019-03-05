---
title: HSE_VERSION_INFO 結構
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 97f34bebae8a486a825d04b23c5a92fbd4aefa42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267832"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO 結構

此結構指向*Amp;os=&over=&hrd=&opt1*中的參數`CHttpServer::GetExtensionVersion`成員函式。 它提供 ISA 版本號碼和 ISA 的文字描述。

## <a name="syntax"></a>語法

```
typedef struct _HSE_VERSION_INFO {
    DWORD dwExtensionVersion;
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;
```

#### <a name="parameters"></a>參數

*dwExtensionVersion*<br/>
ISA 版本號碼

*lpszExtensionDesc*<br/>
ISA 的文字描述。 預設實作提供預留位置文字；覆寫 `CHttpServer::GetExtensionVersion` 以提供您自己的描述。

## <a name="requirements"></a>需求

**標頭：** httpext.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
