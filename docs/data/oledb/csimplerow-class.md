---
title: CSimpleRow 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
dev_langs:
- C++
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 94f90e4c60e5669789caadaaa827b4c12f1f157f
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339779"
---
# <a name="csimplerow-class"></a>CSimpleRow 類別
提供的預設實作，用於資料列控制代碼，用於[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)類別。  
  
## <a name="syntax"></a>語法

```cpp
class CSimpleRow  
```  

## <a name="requirements"></a>需求  
 **Header:** atldb.h  

## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddRefRow](#addrefrow)|將現有的資料列控制代碼的參考計數。|  
|[Compare](#compare)|比較兩個資料列，以查看它們是否參考相同的資料列執行個體。|  
|[CSimpleRow](#csimplerow)|建構函式。|  
|[ReleaseRow](#releaserow)|釋放資料列。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_dwRef](#dwref)|現有的資料列控制代碼的參考計數。|  
|[m_iRowset](#irowset)|表示資料指標的資料列集的索引。|  
  
## <a name="remarks"></a>備註  
 資料列控制代碼在邏輯上的結果資料列的唯一標籤。 `IRowsetImpl` 建立新`CSimpleRow`的要求中的每個資料列[irowsetimpl:: Getnextrows](../../data/oledb/irowsetimpl-getnextrows.md)。 `CSimpleRow` 可以也將取代為您自己的資料列控制代碼的實作的預設樣板引數後，即`IRowsetImpl`。 取代這個類別的唯一需求是將提供的建構函式接受單一參數的類型取代類別**長**。  

## <a name="addrefrow"></a> Csimplerow:: Addrefrow
將現有的資料列控制代碼的參考計數以執行緒安全的方式。  
  
### <a name="syntax"></a>語法  
  
```cpp
DWORD AddRefRow();  
```  

## <a name="compare"></a> Csimplerow:: Compare
比較兩個資料列，以查看它們是否參考相同的資料列執行個體。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT Compare(CSimpleRow* pRow);  
```  
  
#### <a name="parameters"></a>參數  
 *pRow*  
 `CSimpleRow` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 HRESULT 值，通常是 s_ok 時，指出兩個資料列有相同的資料列執行個體，或不同 S_FALSE，指出兩個資料列。 請參閱[IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/library/ms719629.aspx)中*OLE DB 程式設計人員參考*如需其他可能的傳回值。 

## <a name="csimplerow"></a> Csimplerow:: Csimplerow
建構函式。  
  
### <a name="syntax"></a>語法  
  
```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);  
```  
  
#### <a name="parameters"></a>參數  
 *iRowsetCur*  
 [in]編製索引的目前資料列集。  
  
### <a name="remarks"></a>備註  
 設定組[m_iRowset](../../data/oledb/csimplerow-m-irowset.md)要*iRowsetCur*。 

## <a name="releaserow"></a> Csimplerow:: Releaserow
釋放資料列以執行緒安全的方式。  
  
### <a name="syntax"></a>語法  
  
```cpp
DWORD ReleaseRow();  
```  

## <a name="dwref"></a> Csimplerow:: M_dwref
現有的資料列控制代碼的參考計數。  
  
### <a name="syntax"></a>語法  
  
```cpp
DWORD m_dwRef;  
```  

## <a name="irowset"></a> Csimplerow:: M_irowset
表示資料指標的資料列集的索引。  
  
### <a name="syntax"></a>語法  
  
```cpp
KeyType m_iRowset;  
```  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetImpl 類別](../../data/oledb/irowsetimpl-class.md)