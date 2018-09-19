---
title: CBulkRowset 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
dev_langs:
- C++
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3406614b99e2057c9469fe69d02a9fcbe4eae23b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116759"
---
# <a name="cbulkrowset-class"></a>CBulkRowset 類別

擷取和操作處理大量資料擷取的單一呼叫的多個資料列控制代碼的資料列。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
### <a name="parameters"></a>參數  

*TAccessor*<br/>
存取子類別。  

## <a name="requirements"></a>需求  

**標題:** atldbcli.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRows](#addrefrows)|遞增參考計數。|  
|[CBulkRowset](#cbulkrowset)|建構函式。|  
|[MoveFirst](#movefirst)|擷取資料，執行新的大量擷取如有必要的第一列。|  
|[MoveLast](#movelast)|移至最後一個資料列。|  
|[MoveNext](#movenext)|擷取下的一個資料列。|  
|[MovePrev](#moveprev)|移至前一個資料列。|  
|[MoveToBookmark](#movetobookmark)|擷取書籤所標記的資料列或資料列中指定的位移，從該書籤。|  
|[MoveToRatio](#movetoratio)|擷取資料列從資料列集中的小數位置開始。|  
|[ReleaseRows](#releaserows)|設定目前資料列 (`m_nCurrentRow`) 到 0，然後發行所有資料列。|  
|[SetRows](#setrows)|設定一次呼叫所要擷取的資料列控制代碼數目。|  
  
## <a name="example"></a>範例  

下列範例示範使用`CBulkRowset`類別。  
  
[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]  

## <a name="addrefrows"></a> Cbulkrowset:: Addrefrows

呼叫[irowset:: Addrefrows](/previous-versions/windows/desktop/ms719619\(v=vs.85\))遞增目前從大量資料列集擷取的所有資料列的參考計數。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT AddRefRows() throw();  
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。 
  
## <a name="cbulkrowset"></a> Cbulkrowset:: Cbulkrowset

建立新的 `CBulkRowset` 物件並且將預設資料列計數設定為 10。  
  
### <a name="syntax"></a>語法  
  
```cpp
CBulkRowset();  
```  

## <a name="movefirst"></a> Cbulkrowset:: Movefirst

擷取第一個資料列。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveFirst() throw();  
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。

## <a name="movelast"></a> Cbulkrowset:: Movelast

移至最後一個資料列。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveLast() throw();  
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="movenext"></a> Cbulkrowset:: Movenext

擷取下的一個資料列。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveNext() throw();  
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。 當已到達資料列集結尾時，會傳回 DB_S_ENDOFROWSET。 

## <a name="moveprev"></a> Cbulkrowset:: Moveprev

移至前一個資料列。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT MovePrev() throw();  
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="movetobookmark"></a> Cbulkrowset:: Movetobookmark

擷取標示書籤或指定之位移的資料列的資料列 (*lSkip*) 從該書籤。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark, 
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>參數  

*書籤*<br/>
[in] 標記您要從中擷取資料之位置的書籤。  
  
*lSkip*<br/>
[in] 從書籤到目標資料列的資料列計數。 如果*lSkip*為零，將擷取的第一個資料列是已標記書籤的資料列。 如果*lSkip*為 1，將擷取的第一個資料列是資料列已標記書籤的資料列之後。 如果*lSkip*為-1，將擷取的第一個資料列是已標記書籤的資料列之前的資料列。  
  
### <a name="return-value"></a>傳回值  

請參閱[irowset:: Getdata](/previous-versions/windows/desktop/ms716988\(v=vs.85\))中*OLE DB 程式設計人員參考*。 

## <a name="movetoratio"></a> Cbulkrowset:: Movetoratio

擷取資料列從資料列集中的小數位置開始。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator, 
   DBCOUNTITEM nDenominator)throw();  
```  
  
#### <a name="parameters"></a>參數  

*nNumerator*<br/>
[in]用來判斷要從中擷取資料的小數位置分子。  
  
*nDenominator*<br/>
[in]用來判斷要從中擷取資料的小數位置分母。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

`MoveToRatio` 提取資料列大約是根據下列公式：  
  
`(nNumerator *  RowsetSize ) / nDenominator`  
  
其中`RowsetSize`是以資料列的資料列集的大小。 此公式的精確度取決於特定的提供者。 如需詳細資訊，請參閱 < [irowsetscroll::](/previous-versions/windows/desktop/ms709602\(v=vs.85\))中*OLE DB 程式設計人員參考*。   

## <a name="releaserows"></a> Cbulkrowset:: Releaserows

呼叫[irowset:: Releaserows](/previous-versions/windows/desktop/ms719771\(v=vs.85\))遞減目前從大量資料列集擷取的所有資料列的參考計數。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT ReleaseRows() throw();   
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="setrows"></a> Cbulkrowset:: Setrows

設定每個呼叫所擷取的資料列控制代碼數。  
  
### <a name="syntax"></a>語法  
  
```cpp
void SetRows(DBROWCOUNT nRows) throw();  
```  
  
#### <a name="parameters"></a>參數  

*nRows*<br/>
[in] 新的資料列集大小 (資料列數)。  
  
### <a name="remarks"></a>備註  

如果您呼叫這個函式，它必須在開啟資料列集之前。
  
## <a name="see-also"></a>另請參閱  

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)