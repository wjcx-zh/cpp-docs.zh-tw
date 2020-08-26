---
title: CTable 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
- ATL.CTable.Open
- ATL::CTable::Open
- CTable::Open
- CTable.Open
helpviewer_keywords:
- CTable class
- Open method
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
ms.openlocfilehash: a967ef8fa2832afd56442ae4f988ba080d0b2872
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845636"
---
# <a name="ctable-class"></a>CTable 類別

提供方法來直接存取簡單的資料列集 (沒有) 參數的資料列集。

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

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[開啟](#open)|開啟資料表。|

## <a name="remarks"></a>備註

如需如何執行命令以存取資料列集的詳細資訊，請參閱 [CCommand](../../data/oledb/ccommand-class.md) 。

## <a name="ctableopen"></a><a name="open"></a> CTable：： Open

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

*會話*<br/>
在開啟資料表的會話。

*wszTableName*<br/>
在要開啟之資料表的名稱，以 Unicode 字串傳遞。

*szTableName*<br/>
在要開啟之資料表的名稱，以 ANSI 字串傳遞。

*dbid*<br/>
在 `DBID` 要開啟之資料表的。

*pPropSet*<br/>
在 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 結構陣列的指標，其中包含要設定的屬性和值。 請參閱 Windows SDK 中的 OLE DB 程式設計*人員參考*中的[屬性集和屬性群組](/previous-versions/windows/desktop/ms713696(v=vs.85))。 Null 的預設值未指定屬性。

*ulPropSets*<br/>
在在*pPropSet*引數中傳遞的[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))結構數目。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[IOpenRowset：： OpenRowset](/previous-versions/windows/desktop/ms716724(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
