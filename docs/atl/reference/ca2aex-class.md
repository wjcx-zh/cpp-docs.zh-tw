---
title: CA2AEX 類別
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: dfd8967d21005d83b38eeae36cfc147051d7beaf
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168523"
---
# <a name="ca2aex-class"></a>CA2AEX 類別

這個類別是由字串轉換宏 CA2TEX 和 CT2AEX，以及 typedef CA2A 所使用。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```cpp
template <int t_nBufferLength = 128>
class CA2AEX
```

### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
轉譯進程中使用的緩衝區大小。 預設長度為128個位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|建構函式。|
|[CA2AEX：： ~ CA2AEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CA2AEX：： operator LPSTR](#operator_lpstr)|轉換運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CA2AEX：： m_psz](#m_psz)|儲存來源字串的資料成員。|
|[CA2AEX：： m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存已轉換的字串。|

## <a name="remarks"></a>備註

除非需要額外的功能，否則請在您自己的程式碼中使用 CA2TEX、CT2AEX 或 CA2A。

這個類別包含固定大小的靜態緩衝區，用來儲存轉換的結果。 如果結果太大而無法放入靜態緩衝區，類別會使用**malloc**配置記憶體，當物件超出範圍時釋放記憶體。 這可確保與舊版 ATL 中提供的文字轉換宏不同，此類別可安全地在迴圈中使用，而且不會使堆疊溢位。

如果類別嘗試在堆積上配置記憶體且失敗，則會使用 E_OUTOFMEMORY 的`AtlThrow`引數呼叫。

根據預設，ATL 轉換類別和宏會使用目前線程的 ANSI 字碼頁進行轉換。

下列宏是以這個類別為基礎：

- CA2TEX

- CT2AEX

下列 typedef 是以這個類別為基礎：

- CA2A

如需這些文字轉換宏的討論，請參閱[ATL 和 MFC 字串轉換宏](string-conversion-macros.md)。

## <a name="example"></a>範例

如需使用這些字串轉換宏的範例，請參閱[ATL 和 MFC 字串轉換宏](string-conversion-macros.md)。

## <a name="requirements"></a>需求

**標頭：** atlconv.h。h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

建構函式。

```cpp
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*nCodePage*<br/>
未在此類別中使用。

### <a name="remarks"></a>備註

建立翻譯所需的緩衝區。

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX：： ~ CA2AEX

解構函式。

```cpp
~CA2AEX() throw();
```

### <a name="remarks"></a>備註

釋放配置的緩衝區。

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX：： m_psz

儲存來源字串的資料成員。

```cpp
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX：： m_szBuffer

靜態緩衝區，用來儲存已轉換的字串。

```cpp
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX：： operator LPSTR

轉換運算子。

```cpp
operator LPSTR() const throw();
```

### <a name="return-value"></a>傳回值

傳回文字字串，類型為 LPSTR。

## <a name="see-also"></a>另請參閱

[CA2CAEX 類別](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
