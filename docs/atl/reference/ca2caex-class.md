---
title: CA2CAEX 類別
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: e6c727993b2907aaa551421a5d2d23e372b68917
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319137"
---
# <a name="ca2caex-class"></a>CA2CAEX 類別

此類由字串轉換宏 CA2CTEX 和 CT2CAEX 以及 typedef CA2CA 使用。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<int t_nBufferLength = 128>
class CA2CAEX
```

#### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
翻譯過程中使用的緩衝區的大小。 默認長度為 128 位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CA2CAEX:CA2CAEX](#ca2caex)|建構函式。|
|[CA2CAEX::~CA2CAEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CA2CAEX::運營商LPCSTR](#operator_lpcstr)|轉換運算符。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CA2CAEX:m_psz](#m_psz)|存儲原始碼字串的資料成員。|

## <a name="remarks"></a>備註

除非需要額外的功能,否則在您自己的代碼中使用 CA2CTEX、CT2CAEX 或 CA2CA。

此類在迴圈中使用是安全的,並且不會溢出堆疊。 根據預設，ATL 轉換類別及巨集將使用目前的執行緒 ANSI 字碼頁，來進行轉換。

以下巨集基於此類:

- CA2CTEX

- CT2CAEX

以下類型def基於此類:

- CA2CA

有關這些文字轉換巨集的討論,請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="example"></a>範例

有關使用這些字串轉換巨集的範例,請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="requirements"></a>需求

**標題:** atlconv.h

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a>CA2CAEX:CA2CAEX

建構函式。

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*n代碼頁*<br/>
此類中未使用。

### <a name="remarks"></a>備註

創建轉換所需的緩衝區。

## <a name="ca2caexca2caex"></a><a name="dtor"></a>CA2CAEX::~CA2CAEX

解構函式。

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>備註

釋放分配的緩衝區。

## <a name="ca2caexm_psz"></a><a name="m_psz"></a>CA2CAEX:m_psz

存儲原始碼字串的資料成員。

```
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a>CA2CAEX::運營商LPCSTR

轉換運算符。

```
operator LPCSTR() const throw();
```

### <a name="return-value"></a>傳回值

將文字字串返回為 LPCSTR 類型。

## <a name="see-also"></a>另請參閱

[CA2AEX 類別](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
