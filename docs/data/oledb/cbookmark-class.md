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
ms.openlocfilehash: d3d82ea09b7ed2c1cbaf325906b4f9b480e1eb4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359327"
---
# <a name="cbookmark-class"></a>CBookmark 類別

在其緩衝區中保存書籤值。

## <a name="syntax"></a>語法

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>參數

*nSize*<br/>
書籤緩衝區的大小(以位元組為單位)。 當*nSize*為零時,將在運行時動態創建書籤緩衝區。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CBook 標誌](#cbookmark)|建構函數|
|[GetBuffer](#getbuffer)|檢索指向緩衝區的指標。|
|[GetSize](#getsize)|檢索以位元組為單位的緩衝區大小。|
|[設定書籤](#setbookmark)|設置書籤值。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算符 |](#operator)|將一個`CBookmark`類分配給另一個類。|

## <a name="remarks"></a>備註

`CBookmark<0>`是 樣本專業化`CBookmark`。其緩衝區在運行時動態創建。

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a>CBook標誌::CBookmark

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

第一個函式會將緩衝區設定為 NULL，將緩衝區大小設定為 0。 第二個函數將緩衝區大小設置為*nSize,* 將緩衝區設置為*nSize*位元組的位元組。

> [!NOTE]
> 此功能僅在中`CBookmark<0>`可用。

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a>CBook標誌:取得緩衝區

檢索指向書籤緩衝區的指標。

### <a name="syntax"></a>語法

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>傳回值

指向書籤緩衝區的指標。

## <a name="cbookmarkgetsize"></a><a name="getsize"></a>CBook 標誌:取得 Size

擷取書籤緩衝區的大小。

### <a name="syntax"></a>語法

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>傳回值

以位元組為單位的緩衝區大小。

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a>CBook標誌::設定書籤

將*pBuffer*引用的書籤值複製到緩`CBookmark`衝區 ,並將緩衝區大小設定為*nSize*。

### <a name="syntax"></a>語法

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>參數

*nSize*<br/>
[在]書籤緩衝區的大小。

*pBuffer*<br/>
[在]指向包含書籤值的位元組的指標。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

此功能僅在中`CBookmark<0>`可用。

## <a name="cbookmarkoperator-"></a><a name="operator"></a>CBook標誌::運算符 |

指派 `CBookmark` 物件給另一個。

### <a name="syntax"></a>語法

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>備註

此運算碼僅在 中`CBookmark<0>`才需要。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
