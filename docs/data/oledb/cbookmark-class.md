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
ms.openlocfilehash: 4013e40c364593676ebb099804304ffb2adb42c1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838473"
---
# <a name="cbookmark-class"></a>CBookmark 類別

將書簽值保存在其緩衝區中。

## <a name="syntax"></a>語法

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>參數

*nSize*<br/>
書簽緩衝區的大小（以位元組為單位）。 當 *nSize* 為零時，就會在執行時間以動態方式建立書簽緩衝區。

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[CBookmark](#cbookmark)|函數|
|[GetBuffer](#getbuffer)|擷取緩衝區的指標。|
|[GetSize](#getsize)|抓取緩衝區的大小（以位元組為單位）。|
|[SetBookmark](#setbookmark)|設定書簽值。|

### <a name="operators"></a>運算子

| 名稱 | 描述 |
|-|-|
|[運算子 =](#operator)|將一個 `CBookmark` 類別指派給另一個類別。|

## <a name="remarks"></a>備註

`CBookmark<0>` 是的樣板特製化， `CBookmark` 其緩衝區會在執行時間以動態方式建立。

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a> CBookmark：： CBookmark

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

第一個函式會將緩衝區設定為 NULL，將緩衝區大小設定為 0。 第二個函式會將緩衝區大小設定為 *nSize*，並將緩衝區設定為 *nSize* 位元組的位元組陣列。

> [!NOTE]
> 此函數僅適用于 `CBookmark<0>` 。

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a> CBookmark：： GetBuffer

捕獲書簽緩衝區的指標。

### <a name="syntax"></a>語法

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>傳回值

書簽緩衝區的指標。

## <a name="cbookmarkgetsize"></a><a name="getsize"></a> CBookmark：： GetSize

擷取書籤緩衝區的大小。

### <a name="syntax"></a>語法

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>傳回值

以位元組為單位的緩衝區大小。

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a> CBookmark：： SetBookmark

將 *pBuffer* 所參考的書簽值複製到 `CBookmark` 緩衝區，並將緩衝區大小設定為 *nSize*。

### <a name="syntax"></a>語法

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>參數

*nSize*<br/>
在書簽緩衝區的大小。

*pBuffer*<br/>
在包含書簽值的位元組陣列指標。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

此函數僅適用于 `CBookmark<0>` 。

## <a name="cbookmarkoperator-"></a><a name="operator"></a> CBookmark：： operator =

指派 `CBookmark` 物件給另一個。

### <a name="syntax"></a>語法

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>備註

只有在中才需要此運算子 `CBookmark<0>` 。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
