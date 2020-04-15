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
ms.openlocfilehash: 4f8b9f91e9bc499523fe3484bc76325e2efb8140
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319173"
---
# <a name="ca2aex-class"></a>CA2AEX 類別

此類由字串轉換宏 CA2TEX 和 CT2AEX 以及 typedef CA2A 使用。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
翻譯過程中使用的緩衝區的大小。 默認長度為 128 位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CA2AEX:CA2AEX](#ca2aex)|建構函式。|
|[CA2AEX:*CA2AEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CA2AEX::操作員LPSTR](#operator_lpstr)|轉換運算符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CA2AEX:m_psz](#m_psz)|存儲原始碼字串的資料成員。|
|[CA2AEX:m_szBuffer](#m_szbuffer)|用於儲存轉換後的字串的靜態緩衝區。|

## <a name="remarks"></a>備註

除非需要額外的功能,否則在您自己的代碼中使用 CA2TEX、CT2AEX 或 CA2A。

此類包含一個固定大小的靜態緩衝區,用於存儲轉換的結果。 如果結果太大而無法放入靜態緩衝區中,則類將使用**malloc**分配記憶體,當物件超出範圍時釋放記憶體。 這可確保與早期版本的 ATL 中提供的文本轉換宏不同,此類在迴圈中使用是安全的,並且不會溢出堆疊。

如果類嘗試在堆上分配記憶體而失敗,它將調用`AtlThrow`E_OUTOFMEMORY參數。

默認情況下,ATL 轉換類和宏使用當前線程的 ANSI 代碼頁進行轉換。

以下巨集基於此類:

- CA2TEX

- CT2AEX

以下類型def基於此類:

- CA2A

有關這些文字轉換巨集的討論,請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="example"></a>範例

有關使用這些字串轉換巨集的範例,請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="requirements"></a>需求

**標題:** atlconv.h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX:CA2AEX

建構函式。

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*n代碼頁*<br/>
此類中未使用。

### <a name="remarks"></a>備註

創建轉換所需的緩衝區。

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX:*CA2AEX

解構函式。

```
~CA2AEX() throw();
```

### <a name="remarks"></a>備註

釋放分配的緩衝區。

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX:m_psz

存儲原始碼字串的資料成員。

```
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX:m_szBuffer

用於儲存轉換後的字串的靜態緩衝區。

```
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX::操作員LPSTR

轉換運算符。

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>傳回值

將文字字串返回為 LPSTR 類型。

## <a name="see-also"></a>另請參閱

[CA2CAEX 類別](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
