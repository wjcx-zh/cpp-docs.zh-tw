---
title: CBookmark 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
ms.openlocfilehash: fb2e3ec99471405f9c6521e0b70672c1da1b755c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030137"
---
# <a name="cbookmark-class"></a>CBookmark 類別

保留的書籤值在其緩衝區中。

## <a name="syntax"></a>語法

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>參數

*nSize*<br/>
以位元組為單位的書籤緩衝區的大小。 當*nSize*為零，在執行階段會以動態方式建立書籤緩衝區。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CBookmark](#cbookmark)|建構函式|
|[GetBuffer](#getbuffer)|擷取到緩衝區的指標。|
|[GetSize](#getsize)|擷取以位元組為單位的緩衝區大小。|
|[SetBookmark](#setbookmark)|設定書籤值。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#operator)|會指派一個`CBookmark`到另一個類別。|

## <a name="remarks"></a>備註

`CBookmark<0>` 是的樣板特製化`CBookmark`; 在執行階段以動態方式建立它的緩衝區。

## <a name="cbookmark"></a> Cbookmark:: Cbookmark

建構函式。

### <a name="syntax"></a>語法

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>參數

*nSize*<br/>
[in] 書籤緩衝區的大小 (以位元組為單位)。

### <a name="remarks"></a>備註

第一個函式會設定為 NULL，而且設為 0 的緩衝區大小的緩衝區。 第二個函式會將緩衝區大小設定為*nSize*，將緩衝區的位元組陣列*nSize*位元組。

> [!NOTE]
>  此函式僅供以`CBookmark<0>`。

## <a name="getbuffer"></a> Cbookmark:: Getbuffer

擷取書籤緩衝區的指標。

### <a name="syntax"></a>語法

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>傳回值

書籤緩衝區的指標。

## <a name="getsize"></a> Cbookmark:: Getsize

擷取書籤緩衝區的大小。

### <a name="syntax"></a>語法

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>傳回值

以位元組為單位的緩衝區大小。

## <a name="setbookmark"></a> CBookmark::SetBookmark

將所參考的書籤值複製*pBuffer*要`CBookmark`緩衝區，並將緩衝區大小設定為*nSize*。

### <a name="syntax"></a>語法

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>參數

*nSize*<br/>
[in]書籤緩衝區的大小。

*pBuffer*<br/>
[in]包含書籤值的位元組陣列指標。

### <a name="return-value"></a>傳回值

標準的 HRESULT。

### <a name="remarks"></a>備註

此函式僅供以`CBookmark<0>`。

## <a name="operator"></a> Cbookmark:: Operator =

指派 `CBookmark` 物件給另一個。

### <a name="syntax"></a>語法

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>備註

此運算子只有在需要`CBookmark<0>`。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)