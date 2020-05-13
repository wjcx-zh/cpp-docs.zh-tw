---
title: 註冊表資料交換巨集
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
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326075"
---
# <a name="registry-data-exchange-macros"></a>註冊表資料交換巨集

這些宏執行註冊表數據交換操作。

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|標記註冊表數據交換映射的開頭。|
|[END_RDX_MAP](#end_rdx_map)|標記註冊表數據交換映射的末尾。|
|[RDX_BINARY](#rdx_binary)|將指定的註冊表項與 BYTE 類型的指定成員變數關聯。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|將指定的註冊表項與 CString 類型的指定成員變數關聯。|
|[RDX_DWORD](#rdx_dword)|將指定的註冊表項與 DWORD 類型的指定成員變數關聯。|
|[RDX_TEXT](#rdx_text)|將指定的註冊表項與 TCHAR 類型的指定成員變數關聯。|

## <a name="requirements"></a>需求

**標題:** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

標記註冊表數據交換映射的開頭。

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>備註

以下巨集用於註冊表資料交換對應中讀取與寫入系統註冊表中的項目:

|巨集|描述|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|將指定的註冊表項與 BYTE 類型的指定成員變數關聯。|
|[RDX_DWORD](#rdx_dword)|將指定的註冊表項與 DWORD 類型的指定成員變數關聯。|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|將指定的註冊表項與 CString 類型的指定成員變數關聯。|
|[RDX_TEXT](#rdx_text)|將指定的註冊表項與 TCHAR 類型的指定成員變數關聯。|

當代碼需要在系統註冊表和 RDX 映射中指定的變數之間交換數據時,應使用全域函數[RegistryDataExchange,](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏創建的相同名稱的成員函數。

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

標記註冊表數據交換映射的末尾。

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

將指定的註冊表項與 BYTE 類型的指定成員變數關聯。

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*根鍵*<br/>
註冊表密鑰根。

*子鍵*<br/>
註冊表子項。

*值名稱*<br/>
註冊表項。

*成員*<br/>
要與指定的註冊表項關聯的成員變數。

*member_size*<br/>
成員變數的大小(以位元組為單位)。

### <a name="remarks"></a>備註

此宏與BEGIN_RDX_MAP和END_RDX_MAP宏結合使用,用於將成員變數與給定的註冊表項相關聯。 全域函數[RegistryDataExchange,](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏創建的同名成員函數,應用於在 RDX 映射中系統註冊表和成員變數之間執行數據交換。

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

將指定的註冊表項與 CString 類型的指定成員變數關聯。

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*根鍵*<br/>
註冊表密鑰根。

*子鍵*<br/>
註冊表子項。

*值名稱*<br/>
註冊表項。

*成員*<br/>
要與指定的註冊表項關聯的成員變數。

*member_size*<br/>
成員變數的大小(以位元組為單位)。

### <a name="remarks"></a>備註

此宏與BEGIN_RDX_MAP和END_RDX_MAP宏結合使用,用於將成員變數與給定的註冊表項相關聯。 全域函數[RegistryDataExchange,](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏創建的同名成員函數,應用於在 RDX 映射中系統註冊表和成員變數之間執行數據交換。

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

將指定的註冊表項與 DWORD 類型的指定成員變數關聯。

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*根鍵*<br/>
註冊表密鑰根。

*子鍵*<br/>
註冊表子項。

*值名稱*<br/>
註冊表項。

*成員*<br/>
要與指定的註冊表項關聯的成員變數。

*member_size*<br/>
成員變數的大小(以位元組為單位)。

### <a name="remarks"></a>備註

此宏與BEGIN_RDX_MAP和END_RDX_MAP宏結合使用,用於將成員變數與給定的註冊表項相關聯。 全域函數[RegistryDataExchange,](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏創建的同名成員函數,應用於在 RDX 映射中系統註冊表和成員變數之間執行數據交換。

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

將指定的註冊表項與 TCHAR 類型的指定成員變數關聯。

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>參數

*根鍵*<br/>
註冊表密鑰根。

*子鍵*<br/>
註冊表子項。

*值名稱*<br/>
註冊表項。

*成員*<br/>
要與指定的註冊表項關聯的成員變數。

*member_size*<br/>
成員變數的大小(以位元組為單位)。

### <a name="remarks"></a>備註

此宏與BEGIN_RDX_MAP和END_RDX_MAP宏結合使用,用於將成員變數與給定的註冊表項相關聯。 全域函數[RegistryDataExchange,](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)或由BEGIN_RDX_MAP和END_RDX_MAP宏創建的同名成員函數,應用於在 RDX 映射中系統註冊表和成員變數之間執行數據交換。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
