---
title: CEnumerator 類別
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: 2a48acb8a961d76c34d2ba85ede5c827c880f400
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214915"
---
# <a name="cenumerator-class"></a>CEnumerator 類別

會使用 OLE DB 列舉值物件，它會公開[ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85))介面，以傳回描述所有資料來源和枚舉器的資料列集。

## <a name="syntax"></a>語法

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[Find](#find)|搜尋可用的提供者（資料來源），尋找具有指定名稱的提供者。|
|[GetMoniker](#getmoniker)|抓取 `IMoniker` 目前記錄的介面。|
|[開啟](#open)|開啟列舉值。|

## <a name="remarks"></a>備註

您可以 `ISourcesRowset` 從這個類別間接取得資料。

## <a name="cenumeratorfind"></a><a name="find"></a>CEnumerator：： Find

在可用提供者中尋找指定的名稱。

### <a name="syntax"></a>語法

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>參數

*szSearchName*<br/>
[in] 要搜尋的名稱。

### <a name="return-value"></a>傳回值

**`true`** 如果找到名稱，則為。 否則為 **`false`** 。

### <a name="remarks"></a>備註

這個名稱會對應至 `SOURCES_NAME` [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85))介面的成員。

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a>CEnumerator：： GetMoniker

剖析顯示名稱，以解壓縮可轉換成名字標記之字串的元件。

### <a name="syntax"></a>語法

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>參數

*ppMoniker*<br/>
脫銷從目前資料列的顯示名稱（[CEnumeratorAccessor：： m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)）剖析的標記。

*lpszDisplayName*<br/>
在要剖析的顯示名稱。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="cenumeratoropen"></a><a name="open"></a>CEnumerator：： Open

系結列舉值的標記（如果有指定），然後藉由呼叫[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85))來抓取列舉值的資料列集。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>參數

*pMoniker*<br/>
在列舉值之標記的指標。

*pClsid*<br/>
在列舉值的指標 `CLSID` 。

*列舉值*<br/>
在列舉值的參考。

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="see-also"></a>另請參閱

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
