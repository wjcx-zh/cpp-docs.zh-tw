---
title: 登錄資料交換宏
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: 507db77b525c526fe1cd47c7d75c34e15a6a0628
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834540"
---
# <a name="registry-data-exchange-macros"></a>登錄資料交換宏

這些宏會執行登錄資料交換作業。

|名稱|描述|
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|標示登錄資料交換對應的開頭。|
|[END_RDX_MAP](#end_rdx_map)|標示登錄資料交換對應的結尾。|
|[RDX_BINARY](#rdx_binary)|將指定的登錄專案與類型為 BYTE 的指定成員變數產生關聯。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|將指定的登錄專案與類型 CString 的指定成員變數產生關聯。|
|[RDX_DWORD](#rdx_dword)|將指定的登錄專案與類型為 DWORD 的指定成員變數產生關聯。|
|[RDX_TEXT](#rdx_text)|將指定的登錄專案與型別 TCHAR 的指定成員變數產生關聯。|

## <a name="requirements"></a>規格需求

**標頭：** atlplus。h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a> BEGIN_RDX_MAP

標示登錄資料交換對應的開頭。

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>備註

下列宏會在登錄資料交換對應中用來讀取和寫入系統登錄中的專案：

|巨集|描述|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|將指定的登錄專案與類型為 BYTE 的指定成員變數產生關聯。|
|[RDX_DWORD](#rdx_dword)|將指定的登錄專案與類型為 DWORD 的指定成員變數產生關聯。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|將指定的登錄專案與類型 CString 的指定成員變數產生關聯。|
|[RDX_TEXT](#rdx_text)|將指定的登錄專案與型別 TCHAR 的指定成員變數產生關聯。|

每當您的程式碼需要在系統登錄與 RDX 對應中指定的變數之間交換資料時，就應該使用全域函式 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)（或 BEGIN_RDX_MAP 和 END_RDX_MAP 宏所建立之相同名稱的成員函式）。

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a> END_RDX_MAP

標示登錄資料交換對應的結尾。

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a> RDX_BINARY

將指定的登錄專案與類型為 BYTE 的指定成員變數產生關聯。

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*rootkey*<br/>
登錄機碼根目錄。

*子機碼*<br/>
登錄子機碼。

*valuename*<br/>
登錄機碼。

*成員*<br/>
要與指定的登錄專案相關聯的成員變數。

*member_size*<br/>
成員變數的大小（以位元組為單位）。

### <a name="remarks"></a>備註

這個宏會與 BEGIN_RDX_MAP 搭配使用，並 END_RDX_MAP 宏將成員變數與指定的登錄專案產生關聯。 全域函式 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)（或 BEGIN_RDX_MAP 和 END_RDX_MAP 宏所建立之相同名稱的成員函式），應該用來在系統登錄與 RDX 對應中的成員變數之間執行資料交換。

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a> RDX_CSTRING_TEXT

將指定的登錄專案與類型 CString 的指定成員變數產生關聯。

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*rootkey*<br/>
登錄機碼根目錄。

*子機碼*<br/>
登錄子機碼。

*valuename*<br/>
登錄機碼。

*成員*<br/>
要與指定的登錄專案相關聯的成員變數。

*member_size*<br/>
成員變數的大小（以位元組為單位）。

### <a name="remarks"></a>備註

這個宏會與 BEGIN_RDX_MAP 搭配使用，並 END_RDX_MAP 宏將成員變數與指定的登錄專案產生關聯。 全域函式 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)（或 BEGIN_RDX_MAP 和 END_RDX_MAP 宏所建立之相同名稱的成員函式），應該用來在系統登錄與 RDX 對應中的成員變數之間執行資料交換。

## <a name="rdx_dword"></a><a name="rdx_dword"></a> RDX_DWORD

將指定的登錄專案與類型為 DWORD 的指定成員變數產生關聯。

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*rootkey*<br/>
登錄機碼根目錄。

*子機碼*<br/>
登錄子機碼。

*valuename*<br/>
登錄機碼。

*成員*<br/>
要與指定的登錄專案相關聯的成員變數。

*member_size*<br/>
成員變數的大小（以位元組為單位）。

### <a name="remarks"></a>備註

這個宏會與 BEGIN_RDX_MAP 搭配使用，並 END_RDX_MAP 宏將成員變數與指定的登錄專案產生關聯。 全域函式 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)（或 BEGIN_RDX_MAP 和 END_RDX_MAP 宏所建立之相同名稱的成員函式），應該用來在系統登錄與 RDX 對應中的成員變數之間執行資料交換。

## <a name="rdx_text"></a><a name="rdx_text"></a> RDX_TEXT

將指定的登錄專案與型別 TCHAR 的指定成員變數產生關聯。

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*rootkey*<br/>
登錄機碼根目錄。

*子機碼*<br/>
登錄子機碼。

*valuename*<br/>
登錄機碼。

*成員*<br/>
要與指定的登錄專案相關聯的成員變數。

*member_size*<br/>
成員變數的大小（以位元組為單位）。

### <a name="remarks"></a>備註

這個宏會與 BEGIN_RDX_MAP 搭配使用，並 END_RDX_MAP 宏將成員變數與指定的登錄專案產生關聯。 全域函式 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)（或 BEGIN_RDX_MAP 和 END_RDX_MAP 宏所建立之相同名稱的成員函式），應該用來在系統登錄與 RDX 對應中的成員變數之間執行資料交換。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
