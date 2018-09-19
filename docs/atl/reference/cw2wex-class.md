---
title: CW2WEX 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f230e66689578f1b7ea95326d9bc73efc8746c0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093039"
---
# <a name="cw2wex-class"></a>CW2WEX 類別

這個類別會使用字串轉換巨集 CW2TEX CT2WEX 和 typedef CW2W。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>參數

*t_nBufferLength*<br/>
轉譯程序中使用的緩衝區大小。 預設長度為 128 位元組。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|建構函式。|
|[CW2WEX:: ~ CW2WEX](#dtor)|解構函式。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|轉換運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|儲存在來源字串資料成員。|
|[CW2WEX::m_szBuffer](#m_szbuffer)|靜態緩衝區，用來儲存已轉換的字串。|

## <a name="remarks"></a>備註

除非需要額外的功能，使用 CW2TEX、 CT2WEX 或 CW2W 程式碼中。

這個類別包含固定大小的靜態緩衝區可用來儲存轉換的結果。 如果結果太大而無法放入靜態緩衝區，類別配置的記憶體使用**malloc**，當物件超出範圍時，即釋放記憶體。 這可確保，不同於文字轉換巨集可在舊版的 ATL，這個類別能夠安全地在迴圈中使用，而且它不會堆疊溢位。

如果類別嘗試失敗與堆積上配置記憶體時，它會呼叫`AtlThrow`E_OUTOFMEMORY 引數。

根據預設，ATL 轉換類別和巨集會使用目前的執行緒 ANSI 字碼頁轉換。

下列巨集根據此類別：

- CW2TEX

- CT2WEX

下列的 typedef 根據此類別：

- CW2W

如需這些文字轉換巨集的討論，請參閱 < [ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)。

## <a name="example"></a>範例

請參閱[ATL 和 MFC 字串轉換巨集](string-conversion-macros.md)如需使用這些字串轉換巨集的範例。

## <a name="requirements"></a>需求

**標頭：** atlconv.h

##  <a name="cw2wex"></a>  CW2WEX::CW2WEX

建構函式。

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>參數

*psz*<br/>
要轉換的文字字串。

*nCodePage*<br/>
字碼頁。 不使用這個類別中。

### <a name="remarks"></a>備註

建立做為轉換所需的緩衝區。

##  <a name="dtor"></a>  CW2WEX:: ~ CW2WEX

解構函式...

```
~CW2WEX() throw();
```

### <a name="remarks"></a>備註

釋放配置的緩衝區。

##  <a name="m_psz"></a>  CW2WEX::m_psz

儲存在來源字串資料成員。

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2WEX::m_szBuffer

靜態緩衝區，用來儲存已轉換的字串。

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>  CW2WEX::operator LPWSTR

轉換運算子。

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>傳回值

傳回文字字串，當輸入 LPWSTR。

## <a name="see-also"></a>另請參閱

[CA2AEX 類別](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 類別](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 類別](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 類別](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 類別](../../atl/reference/cw2cwex-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
