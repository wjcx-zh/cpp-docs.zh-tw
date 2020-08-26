---
title: CStreamRowset 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
ms.openlocfilehash: 304dfe0e026a9fbba899c1ef17c06cf1baf1529b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841047"
---
# <a name="cstreamrowset-class"></a>CStreamRowset 類別

用於或宣告 `CCommand` `CTable` 。

## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>參數

*TAccessor*<br/>
存取子類別。

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

| 名稱 | 描述 |
|-|-|
|[CStreamRowset](#cstreamrowset)|建構函式。 具現化並初始化 `CStreamRowset` 物件。|
|[關閉](#close)|釋放類別中的 [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) 介面指標。|

## <a name="remarks"></a>備註

`CStreamRowset`在您的或宣告中使用 `CCommand` `CTable` ，例如：

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

或

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` 傳回 `ISequentialStream` 儲存在中的指標 `m_spStream` 。 然後，您可以使用 `Read` 方法，以 XML 格式來取得 (的 Unicode 字串) 資料。 例如：

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 會執行 XML 格式，而且會將資料列集的所有資料行和所有資料列傳回為一個 XML 字串。

> [!NOTE]
> 這項功能僅適用于 SQL Server 2000。

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a> CStreamRowset：： CStreamRowset

具現化並初始化 `CStreamRowset` 物件。

### <a name="syntax"></a>語法

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a> CStreamRowset：： Close

釋放類別中的 [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) 介面指標。

### <a name="syntax"></a>語法

```cpp
void Close();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
