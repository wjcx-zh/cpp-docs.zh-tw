---
title: CAccessorRowset 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- FreeRecordMemory
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afae1f91907e8fd22640dd87fe607a067900edfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024641"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 類別

封裝資料列集和其相關聯的存取子，單一類別中。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CNoAccessor, 
   template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
```  
  
### <a name="parameters"></a>參數  

*TAccessor*<br/>
存取子類別。  
  
*TRowset*<br/>
資料列集類別。  

## <a name="requirements"></a>需求  

**標題:** atldbcli.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[Bind](#bind)|建立繫結 (使用的時機`bBind`指定為**false**中[ccommand:: Open](../../data/oledb/ccommand-open.md))。|  
|[CAccessorRowset](#caccessorrowset)|建構函式。|  
|[關閉](#close)|關閉資料列集和任何存取子。|  
|[FreeRecordMemory](#freerecordmemory)|釋出任何需要先釋放目前記錄中的資料行。|  
|[GetColumnInfo](#getcolumninfo)|Implements [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))。|  
  
## <a name="remarks"></a>備註  

類別`TAccessor`管理存取子。 類別*TRowset*管理資料列集。  

## <a name="bind"></a> Caccessorrowset:: Bind

建立繫結，如果您指定`bBind`作為**假**中[ccommand:: Open](../../data/oledb/ccommand-open.md)。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT Bind();  
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="caccessorrowset"></a> Caccessorrowset:: Caccessorrowset

初始化 `CAccessorRowset` 物件。  
  
### <a name="syntax"></a>語法  
  
```cpp
CAccessorRowset();  
```  

## <a name="close"></a> Caccessorrowset:: Close

釋放使用中的任何存取子和資料列集。  
  
### <a name="syntax"></a>語法  
  
```cpp
void Close();  
```  
  
### <a name="remarks"></a>備註  

釋放任何相關聯的記憶體。  

## <a name="freerecordmemory"></a> Caccessorrowset:: Freerecordmemory

釋出任何需要先釋放目前記錄中的資料行。  
  
### <a name="syntax"></a>語法  
  
```cpp
void FreeRecordMemory();  
```  

## <a name="getcolumninfo"></a> Caccessorrowset:: Getcolumninfo

從開啟的資料列集取得資料行資訊。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns, 
   DBCOLUMNINFO** ppColumnInfo, 
   LPOLESTR* ppStrings) const; 
    
HRESULT GetColumnInfo(DBORDINAL* pColumns, 
   DBCOLUMNINFO** ppColumnInfo);  
```  
  
#### <a name="parameters"></a>參數  

請參閱[icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

使用者必須釋放字串緩衝區與傳回的資料行資訊。 使用此方法的第二個版本，當您使用[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)和需要覆寫繫結。  
  
如需詳細資訊，請參閱 < [icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)