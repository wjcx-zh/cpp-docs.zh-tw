---
title: CRestrictions 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: 9fb911b469497a007550c042ade97b5a463e78fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220440"
---
# <a name="crestrictions-class"></a>CRestrictions 類別

泛型類別，可讓您指定架構資料列集的限制。

## <a name="syntax"></a>語法

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>參數

*T*<br/>
用於存取子的類別。

*nRestrictions*<br/>
架構資料列集的限制資料行數目。

*pguid*<br/>
架構之 GUID 的指標。

## <a name="requirements"></a>需求

**標頭：** atldbsch.h。h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[開啟](#open)|根據使用者提供的限制傳回結果集。|

## <a name="crestrictionsopen"></a><a name="open"></a>CRestrictions：： Open

根據使用者提供的限制傳回結果集。

### <a name="syntax"></a>語法

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>參數

*本次*<br/>
在指定用來連接到資料來源的現有會話物件。

*lpszParam*<br/>
在指定架構資料列集的限制。

*bBind*<br/>
在指定是否要自動系結資料行對應。 預設值為 **`true`** ，這會自動系結資料行對應。 將*bBind*設定為可防止自動系結資料 **`false`** 行對應，讓您可以手動系結。 （對 OLAP 使用者而言，手動系結特別重要）。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

您最多可以在架構資料列集上指定七個限制。

如需每個架構資料列集上定義之限制的相關資訊，請參閱[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[架構資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
