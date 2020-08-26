---
title: IRowsetLocateImpl 類別
ms.date: 11/04/2016
f1_keywords:
- IRowsetLocateImpl
- ATL.IRowsetLocateImpl.Compare
- IRowsetLocateImpl::Compare
- IRowsetLocateImpl.Compare
- ATL::IRowsetLocateImpl::Compare
- GetRowsAt
- IRowsetLocateImpl.GetRowsAt
- ATL::IRowsetLocateImpl::GetRowsAt
- IRowsetLocateImpl::GetRowsAt
- ATL.IRowsetLocateImpl.GetRowsAt
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
- IRowsetLocateImpl::Hash
- IRowsetLocateImpl.Hash
- m_rgBookmarks
- IRowsetLocateImpl::m_rgBookmarks
- ATL.IRowsetLocateImpl.m_rgBookmarks
- ATL::IRowsetLocateImpl::m_rgBookmarks
- IRowsetLocateImpl.m_rgBookmarks
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
- Compare method
- GetRowsAt method
- GetRowsByBookmark method
- Hash method
- m_rgbookmarks
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
ms.openlocfilehash: a45b7ef1a31c3ecf34b15ee35bce48559465a905
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840306"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl 類別

會執行 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) 介面，此介面會從資料列集提取任意資料列。

## <a name="syntax"></a>語法

```cpp
template <
   class T,
   class RowsetInterface,
   class RowClass = CSimpleRow,
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,
   class BookmarkKeyType = LONG,
   class BookmarkType = LONG,
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<
       T,
       RowsetInterface,
       RowClass,
       MapClass>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `IRowsetLocateImpl` 。

*RowsetInterface*<br/>
衍生自的類別 `IRowsetImpl` 。

*RowClass*<br/>
的儲存單位 `HROW` 。

*MapClass*<br/>
提供者所保留的所有資料列控制碼的儲存單位。

*BookmarkKeyType*<br/>
書簽的型別，例如 LONG 或 string。 一般書簽的長度必須至少為兩個位元組。  (的單一位元組長度會保留給 OLE DB[標準書簽](/previous-versions/windows/desktop/ms712954(v=vs.85)) `DBBMK_FIRST` 、 `DBBMK_LAST` 和 `DBBMK_INVALID` 。 ) 

*BookmarkType*<br/>
用於維護書簽對資料關聯性的對應機制。

*BookmarkMapClass*<br/>
書簽所保留的所有資料列控制碼的儲存單位。

## <a name="requirements"></a>規格需求

**標頭**： atldb.h。h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[比較](#compare)|比較兩個書簽。|
|[GetRowsAt](#getrowsat)|從書簽中位移所指定的資料列開始提取資料列。|
|[GetRowsByBookmark](#getrowsbybookmark)|提取符合指定書簽的資料列。|
|[雜湊](#hash)|傳回指定書簽的雜湊值。|

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|-|-|
|[m_rgBookmarks](#rgbookmarks)|書簽的陣列。|

## <a name="remarks"></a>備註

`IRowsetLocateImpl` 是 [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) 介面的 OLE DB 範本執行。 `IRowsetLocate` 用來從資料列集提取任意資料列。 未執行此介面的資料列集是資料列 `sequential` 集。 當資料 `IRowsetLocate` 列集出現時，資料行0是資料列的書簽; 讀取此資料行會取得可用於重新置放至相同資料列的書簽值。

`IRowsetLocateImpl` 用來在提供者中執行書簽支援。 書簽是在資料列集上 (索引的預留位置) 可讓取用者快速地返回資料列，以允許對資料進行高速存取。 此提供者會決定可唯一識別資料列的書簽。 `IRowsetLocateImpl`您可以使用方法來比較書簽、依位移提取資料列、依書簽提取資料列，以及傳回書簽的雜湊值。

若要支援資料列集中的 OLE DB 書簽，請讓資料列集繼承自這個類別。

如需有關實施書簽支援的詳細資訊，請參閱*Visual C++* 程式設計人員指南中的[書簽支援](../../data/oledb/provider-support-for-bookmarks.md)，以及 OLE DB 程式設計人員在 Platform SDK 中的*參考*中的[書簽](/previous-versions/windows/desktop/ms709728(v=vs.85))。

## <a name="irowsetlocateimplcompare"></a><a name="compare"></a> IRowsetLocateImpl：： Compare

比較兩個書簽。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (Compare )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmark1,
   const BYTE* pBookmark1,
   DBBKMARK cbBookmark2,
   const BYTE* pBookmark2,
   DBCOMPARE* pComparison);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetLocate：： Compare](/previous-versions/windows/desktop/ms709539(v=vs.85)) 。

### <a name="remarks"></a>備註

其中一個書簽可以是標準的 OLE DB 定義 [標準書簽](/previous-versions/windows/desktop/ms712954(v=vs.85)) (`DBBMK_FIRST` 、 `DBBMK_LAST` 或 `DBBMK_INVALID`) 。 傳回的值 `pComparison` 指出兩個書簽之間的關聯性：

- DBCOMPARE_LT (`cbBookmark1` 之前 `cbBookmark2` 。 ) 

- DBCOMPARE_EQ (`cbBookmark1` 等於 `cbBookmark2` 。 ) 

- DBCOMPARE_GT (`cbBookmark1` `cbBookmark2` 。 ) 

- DBCOMPARE_NE (書簽相等且未排序。 ) 

- DBCOMPARE_NOTCOMPARABLE (無法比較書簽。 ) 

## <a name="irowsetlocateimplgetrowsat"></a><a name="getrowsat"></a> IRowsetLocateImpl：： GetRowsAt

從書簽中位移所指定的資料列開始提取資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetRowsAt )(HWATCHREGION /* hReserved1 */,
   HCHAPTER hReserved2,
   DBBKMARK cbBookmark,
   const BYTE* pBookmark,
   DBROWOFFSET lRowsOffset,
   DBROWCOUNT cRows,
   DBCOUNTITEM* pcRowsObtained,
   HROW** prghRows);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[IRowsetLocate：： GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85)) 。

### <a name="remarks"></a>備註

若要改為從游標位置提取，請使用 [IRowset：： GetRowsAt](/previous-versions/windows/desktop/ms723031(v=vs.85))。

`IRowsetLocateImpl::GetRowsAt` 不會變更游標位置。

## <a name="irowsetlocateimplgetrowsbybookmark"></a><a name="getrowsbybookmark"></a> IRowsetLocateImpl：： GetRowsByBookmark

提取一或多個符合指定書簽的資料列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,
   DBCOUNTITEM cRows,
   const DBBKMARK rgcbBookmarks[],
   const BYTE* rgpBookmarks,
   HROW rghRows[],
   DBROWSTATUS* rgRowStatus[]);
```

#### <a name="parameters"></a>參數

*hReserved*<br/>
在對應至[IRowsetLocate：： GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85))的*hChapter*參數。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetLocate：： GetRowsByBookmark](/previous-versions/windows/desktop/ms725420(v=vs.85)) 。

### <a name="remarks"></a>備註

書簽可以是您所定義的值，也可以是 (或) 的 OLE DB [標準書簽](/previous-versions/windows/desktop/ms712954(v=vs.85)) `DBBMK_FIRST` `DBBMK_LAST` 。 不會變更游標位置。

## <a name="irowsetlocateimplhash"></a><a name="hash"></a> IRowsetLocateImpl：： Hash

傳回指定書簽的雜湊值。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (Hash )(HCHAPTER /* hReserved */,
   DBBKMARK cbBookmarks,
   const DBBKMARK* rgcbBookmarks[],
   const BYTE* rgpBookmarks[],
   DBHASHVALUE rgHashValues[],
   DBROWSTATUS rgBookmarkStatus[]);
```

#### <a name="parameters"></a>參數

*hReserved*<br/>
在對應至[IRowsetLocate：： Hash](/previous-versions/windows/desktop/ms709697(v=vs.85))的*hChapter*參數。

如需其他參數，請參閱 OLE DB 程式設計*人員參考*中的[IRowsetLocate：： Hash](/previous-versions/windows/desktop/ms709697(v=vs.85)) 。

## <a name="irowsetlocateimplm_rgbookmarks"></a><a name="rgbookmarks"></a> IRowsetLocateImpl：： m_rgBookmarks

書簽的陣列。

### <a name="syntax"></a>語法

```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;
```

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate： IRowset](/previous-versions/windows/desktop/ms721190(v=vs.85)) 
[書簽的提供者支援](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[書籤](/previous-versions/windows/desktop/ms709728(v=vs.85))
