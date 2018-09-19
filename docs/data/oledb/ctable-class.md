---
title: CTable 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
dev_langs:
- C++
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c94152a9322b64acafe91e1fb0eb34ab82aa2902
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081295"
---
# <a name="ctable-class"></a>CTable 類別

提供方法來直接存取簡單的資料列集 （不含任何參數的其中一個）。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CNoAccessor, 
            template <typename T> class TRowset = CRowset>  
class CTable :  
   public CAccessorRowset <TAccessor, TRowset>  
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
|[開啟](#open)|開啟資料表。|  
  
## <a name="remarks"></a>備註  

請參閱[CCommand](../../data/oledb/ccommand-class.md)如需有關如何執行命令來存取資料列集資訊。  

## <a name="open"></a> Ctable:: Open

開啟資料表。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  

HRESULT Open(const CSession& session,  
   LPCSTR szTableName,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  

HRESULT Open(const CSession& session,  
   DBID& dbid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG ulPropSets = 0) throw ();  
```  
  
#### <a name="parameters"></a>參數  

*工作階段*<br/>
[in]開啟該表格中的工作階段。  
  
*wszTableName*<br/>
[in]若要開啟，資料表名稱傳遞為 Unicode 字串。  
  
*szTableName*<br/>
[in]若要開啟，資料表名稱傳遞為 ANSI 字串。  
  
*dbid*<br/>
[in]`DBID`来開啟的資料表。  
  
*pPropSet*<br/>
[in]陣列的指標[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))結構，其中包含要設定屬性和值。 請參閱[的屬性集和屬性群組](/previous-versions/windows/desktop/ms713696\(v=vs.85\))中*OLE DB 程式設計人員參考*Windows SDK 中。 預設值是 NULL 指定任何屬性。  
  
*ulPropSets*<br/>
[in]數目[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))結構傳入*Dbpropset*引數。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

如需詳細資訊，請參閱 < [iopenrowset:: Openrowset](/previous-versions/windows/desktop/ms716724\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)   