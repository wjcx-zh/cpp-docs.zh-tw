---
title: CW2AEX 類別
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 4dda1cb9e54c44f7940475660bc629192b9ead61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496271"
---
# <a name="cw2aex-class"></a>CW2AEX 類別

這個類別是由字串轉換宏 CT2AEX、CW2TEX、CW2CTEX 和 CT2CAEX, 以及 typedef CW2A 所使用。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
轉譯進程中使用的緩衝區大小。 預設長度為128個位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|建構函式。|
|[CW2AEX::~CW2AEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CW2AEX:: operator LPSTR](#operator_lpstr)|轉換運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|儲存來源字串的資料成員。|
|[CW2AEX::m_szBuffer](#m_szbuffer)|靜態緩衝區, 用來儲存已轉換的字串。|

## <a name="remarks"></a>備註

除非需要額外的功能, 否則請在您的程式碼中使用 CT2AEX、CW2TEX、CW2CTEX、CT2CAEX 或 CW2A。

這個類別包含固定大小的靜態緩衝區, 用來儲存轉換的結果。 如果結果太大而無法放入靜態緩衝區, 類別會使用**malloc**配置記憶體, 當物件超出範圍時釋放記憶體。 這可確保與舊版 ATL 中提供的文字轉換宏不同, 此類別可安全地在迴圈中使用, 而且不會使堆疊溢位。

如果類別嘗試在堆積上配置記憶體且失敗, 則會使用 E_OUTOFMEMORY 的`AtlThrow`引數呼叫。

根據預設, ATL 轉換類別和宏會使用目前線程的 ANSI 字碼頁進行轉換。 如果您想要覆寫特定轉換的行為, 請將字碼頁指定為類別之函式的第二個參數。

下列宏是以這個類別為基礎:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

下列 typedef 是以這個類別為基礎:

- CW2A

如需這些文字轉換宏的討論, 請參閱[ATL 和 MFC 字串轉換宏](string-conversion-macros.md)。

## <a name="example"></a>範例

如需使用這些字串轉換宏的範例, 請參閱[ATL 和 MFC 字串轉換宏](string-conversion-macros.md)。

## <a name="requirements"></a>需求

**標頭:** atlconv.h。h

##  <a name="cw2aex"></a>  CW2AEX::CW2AEX

建構函式。

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*nCodePage*<br/>
用來執行轉換的字碼頁。 如需詳細資訊, 請參閱 Windows SDK 函數[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)的字碼頁參數討論。

### <a name="remarks"></a>備註

配置用於轉譯進程的緩衝區。

##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX

解構函式。

```
~CW2AEX() throw();
```

### <a name="remarks"></a>備註

釋放配置的緩衝區。

##  <a name="m_psz"></a>  CW2AEX::m_psz

儲存來源字串的資料成員。

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer

靜態緩衝區, 用來儲存已轉換的字串。

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>CW2AEX:: operator LPSTR

轉換運算子。

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>傳回值

傳回文字字串, 類型為 LPSTR。

## <a name="see-also"></a>另請參閱

[CA2AEX 類別](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 類別](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 類別](../../atl/reference/cw2wex-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
