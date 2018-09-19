---
title: IRowsetLocateImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6a8e41561057250f4936e8e72a14f0324cfcdac1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065307"
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl 類別

實作 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190\(v=vs.85\))介面，它會從資料列集提取任意的資料列。  
  
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
類別衍生自`IRowsetLocateImpl`。  
  
*RowsetInterface*<br/>
類別衍生自`IRowsetImpl`。  
  
*RowClass*<br/>
儲存體單位`HROW`。  
  
*MapClass*<br/>
提供者所持有的所有資料列控制代碼儲存體單位。  
  
*BookmarkKeyType*<br/>
書籤，例如長時間或字串的型別。 一般的書籤必須具有至少兩個位元組的長度。 (單位元組長度保留供 OLE DB[標準的書籤](/previous-versions/windows/desktop/ms712954\(v=vs.85\))`DBBMK_FIRST`， `DBBMK_LAST`，和`DBBMK_INVALID`。)  
  
*BookmarkType*<br/>
維護書籤的資料關聯性的對應機制。  
  
*BookmarkMapClass*<br/>
書籤所持有的所有資料列控制代碼儲存體單位。  

## <a name="requirements"></a>需求  

**標頭**： 為 atldb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[Compare](#compare)|比較兩個書籤。|  
|[GetRowsAt](#getrowsat)|擷取從書籤中位移所指定的資料列開始的資料列。|  
|[GetRowsByBookmark](#getrowsbybookmark)|擷取符合指定的書籤的資料列。|  
|[雜湊](#hash)|傳回雜湊值，指定的書籤。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_rgBookmarks](#rgbookmarks)|書籤的陣列。|  
  
## <a name="remarks"></a>備註  

`IRowsetLocateImpl` 是 OLE DB 樣板實作[IRowsetLocate](/previous-versions/windows/desktop/ms721190\(v=vs.85\))介面。 `IRowsetLocate` 用來從資料列集擷取任意資料列。 未實作此介面的資料列集是`sequential`資料列集。 當`IRowsetLocate`存在於資料列集，資料行 0 是資料列的書籤，閱讀這篇專欄，就會取得可用來重新定位到相同的資料列的書籤值。  
  
`IRowsetLocateImpl` 用來實作提供者中的書籤的支援。 書籤是預留位置 （索引資料列集） 可讓取用者快速地返回資料列，讓高速資料的存取權。 提供者會決定哪些書籤可以唯一識別資料列。 使用`IRowsetLocateImpl`方法，您可以比較的書籤，提取資料列的位移依書籤，提取資料列，並傳回書籤的雜湊值。  
  
若要支援 OLE DB 的書籤中的資料列集，請繼承自這個類別的資料列集。  
  
如需實作的書籤支援的詳細資訊，請參閱[提供者支援書籤](../../data/oledb/provider-support-for-bookmarks.md)中*Visual c + + 程式設計人員指南*並[書籤](/previous-versions/windows/desktop/ms709728\(v=vs.85\))中*OLE DB 程式設計人員參考*平台 SDK 中。  

## <a name="compare"></a> Irowsetlocateimpl:: Compare

比較兩個書籤。  
  
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

請參閱[IRowsetLocate::Compare](/previous-versions/windows/desktop/ms709539\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  

其中一個書籤可以是一種標準 OLE DB 定義[標準的書籤](/previous-versions/windows/desktop/ms712954\(v=vs.85\))(`DBBMK_FIRST`， `DBBMK_LAST`，或`DBBMK_INVALID`)。 中傳回的值`pComparison`表示兩個書籤之間的關聯性：  
  
- DBCOMPARE_LT (`cbBookmark1`之前`cbBookmark2`。)  
  
- DBCOMPARE_EQ (`cbBookmark1`等於`cbBookmark2`。)  
  
- DBCOMPARE_GT (`cbBookmark1`晚`cbBookmark2`。)  
  
- DBCOMPARE_NE （書籤都相等和不排序）。  
  
- DBCOMPARE_NOTCOMPARABLE （無法比較這些書籤）。 

## <a name="getrowsat"></a> Irowsetlocateimpl:: Getrowsat

擷取從書籤中位移所指定的資料列開始的資料列。  
  
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

請參閱[irowsetlocate:: Getrowsat](/previous-versions/windows/desktop/ms723031\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  

若要改為擷取資料指標位置，使用[IRowset::GetRowsAt](/previous-versions/windows/desktop/ms723031\(v=vs.85\))。  
  
`IRowsetLocateImpl::GetRowsAt` 不會變更資料指標位置。 

## <a name="getrowsbybookmark"></a> Irowsetlocateimpl:: Getrowsbybookmark

擷取符合指定的書籤的一或多個資料列。  
  
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
[in]對應至*hChapter*參數來[irowsetlocate:: Getrowsbybookmark](/previous-versions/windows/desktop/ms725420\(v=vs.85\))。  
  
其他參數，請參閱[irowsetlocate:: Getrowsbybookmark](/previous-versions/windows/desktop/ms725420\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="remarks"></a>備註  

書籤可以是您定義的值或 OLE DB[標準的書籤](/previous-versions/windows/desktop/ms712954\(v=vs.85\))(`DBBMK_FIRST`或`DBBMK_LAST`)。 不會變更資料指標位置。  

## <a name="hash"></a> Irowsetlocateimpl:: Hash

傳回雜湊值，指定的書籤。  
  
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
[in]對應至*hChapter*參數來[IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697\(v=vs.85\))。  
  
其他參數，請參閱[IRowsetLocate::Hash](/previous-versions/windows/desktop/ms709697\(v=vs.85\))中*OLE DB 程式設計人員參考*。  

## <a name="rgbookmarks"></a> Irowsetlocateimpl:: M_rgbookmarks

書籤的陣列。  
  
### <a name="syntax"></a>語法  
  
```cpp
CAtlArray<DBROWCOUNT> m_rgBookmarks;  
```  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetLocate:IRowset](/previous-versions/windows/desktop/ms721190\(v=vs.85\))   
[提供者書籤支援](../../data/oledb/provider-support-for-bookmarks.md)<br/>
[書籤](/previous-versions/windows/desktop/ms709728\(v=vs.85\))