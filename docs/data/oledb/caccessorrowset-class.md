---
title: CAccessorRowset 類別
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
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
ms.openlocfilehash: 9ad4292b69d0219aa1732638ae250758e4456f4b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843283"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 類別

將資料列集和其相關聯的存取子封裝在單一類別中。

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

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|--|--|
| [綁定](#bind) | 當 `bBind` 指定為 **`false`** [CCommand：： Open](../../data/oledb/ccommand-open.md)) 時，會建立 (所使用的系結。 |
| [CAccessorRowset](#caccessorrowset) | 建構函式。 |
| [關閉](#close) | 關閉資料列集和任何存取子。 |
| [FreeRecordMemory](#freerecordmemory) | 釋出目前記錄中需要釋放的任何資料行。 |
| [GetColumnInfo](#getcolumninfo) | Implements [IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))。 |

## <a name="remarks"></a>備註

類別會 `TAccessor` 管理存取子。 類別 *TRowset* 會管理資料列集。

## <a name="caccessorrowsetbind"></a><a name="bind"></a> CAccessorRowset：： Bind

如果您 `bBind` **`false`** 在 [CCommand：： Open](../../data/oledb/ccommand-open.md)中指定為，則建立系結。

### <a name="syntax"></a>語法

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>傳回值

標準 HRESULT。

## <a name="caccessorrowsetcaccessorrowset"></a><a name="caccessorrowset"></a> CAccessorRowset：： CAccessorRowset

初始化 `CAccessorRowset` 物件。

### <a name="syntax"></a>語法

```cpp
CAccessorRowset();
```

## <a name="caccessorrowsetclose"></a><a name="close"></a> CAccessorRowset：： Close

釋放任何作用中存取子和資料列集。

### <a name="syntax"></a>語法

```cpp
void Close();
```

### <a name="remarks"></a>備註

釋放任何相關聯的記憶體。

## <a name="caccessorrowsetfreerecordmemory"></a><a name="freerecordmemory"></a> CAccessorRowset：： FreeRecordMemory

釋出目前記錄中需要釋放的任何資料行。

### <a name="syntax"></a>語法

```cpp
void FreeRecordMemory();
```

## <a name="caccessorrowsetgetcolumninfo"></a><a name="getcolumninfo"></a> CAccessorRowset：： GetColumnInfo

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

請參閱 OLE DB 程式設計*人員參考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 。

### <a name="return-value"></a>傳回值

標準 HRESULT。

### <a name="remarks"></a>備註

使用者必須釋放傳回的資料行資訊和字串緩衝區。 當您使用 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 時，請使用這個方法的第二個版本，且需要覆寫系結。

如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
