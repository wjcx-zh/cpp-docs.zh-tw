---
title: HSE_VERSION_INFO 結構
ms.date: 11/04/2016
f1_keywords:
- HSE_VERSION_INFO
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
ms.openlocfilehash: 6bdb668be037dfaa07e1121e4b61ea332e430e31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577279"
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

