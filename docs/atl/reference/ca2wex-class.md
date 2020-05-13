---
title: CA2WEX 類別
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: a710034c5d94a8fb093a2b6a2a52373e2bab2d6d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168497"
---
# <a name="ca2wex-class"></a>CA2WEX 類別

這個類別是由字串轉換宏 CA2TEX、CA2CTEX、CT2WEX 和 CT2CWEX，以及 typedef CA2W 所使用。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template <int t_nBufferLength = 128>
class CA2WEX
```

### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
轉譯進程中使用的緩衝區大小。 預設長度為128個位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|建構函式。|
|[CA2WEX：： ~ CA2WEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CA2WEX：： operator LPWSTR](#operator_lpwstr)|轉換運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CA2WEX：： m_psz](#m_psz)|儲存來源字串的資料成員。|
|[CA2WEX：： m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存已轉換的字串。|

## <a name="remarks"></a>備註

除非需要額外的功能，否則請在您的程式碼中使用 CA2TEX、CA2CTEX、CT2WEX、CT2CWEX 或 CA2W。

這個類別包含固定大小的靜態緩衝區，用來儲存轉換的結果。 如果結果太大而無法放入靜態緩衝區，類別會使用**malloc**配置記憶體，當物件超出範圍時釋放記憶體。 這可確保與舊版 ATL 中提供的文字轉換宏不同，此類別可安全地在迴圈中使用，而且不會使堆疊溢位。

如果類別嘗試在堆積上配置記憶體且失敗，則會使用 E_OUTOFMEMORY 的`AtlThrow`引數呼叫。

根據預設，ATL 轉換類別和宏會使用目前線程的 ANSI 字碼頁進行轉換。 如果您想要覆寫特定轉換的行為，請將字碼頁指定為類別之函式的第二個參數。

下列宏是以這個類別為基礎：

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

下列 typedef 是以這個類別為基礎：

- CA2W

如需這些文字轉換宏的討論，請參閱[ATL 和 MFC 字串轉換宏](string-conversion-macros.md)。

## <a name="example"></a>範例

如需使用這些字串轉換宏的範例，請參閱[ATL 和 MFC 字串轉換宏](string-conversion-macros.md)。

## <a name="requirements"></a>需求

**標頭：** atlconv.h。h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

建構函式。

```cpp
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*nCodePage*<br/>
用來執行轉換的字碼頁。 如需詳細資訊，請參閱 Windows SDK 函數[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)的字碼頁參數討論。

### <a name="remarks"></a>備註

配置用於轉譯進程的緩衝區。

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX：： ~ CA2WEX

解構函式。

```cpp
~CA2WEX() throw();
```

### <a name="remarks"></a>備註

釋放配置的緩衝區。

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX：： m_psz

儲存來源字串的資料成員。

```cpp
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX：： m_szBuffer

靜態緩衝區，用來儲存已轉換的字串。

```cpp
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX：： operator LPWSTR

轉換運算子。

```cpp
operator LPWSTR() const throw();
```

### <a name="return-value"></a>傳回值

傳回文字字串，類型為 LPWSTR。

## <a name="see-also"></a>另請參閱

[CA2AEX 類別](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 類別](../../atl/reference/ca2caex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
