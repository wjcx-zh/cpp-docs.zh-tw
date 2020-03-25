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
ms.openlocfilehash: 300933fd6d10f5da39d9276db746ab789851a9a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211168"
---
# <a name="cstreamrowset-class"></a>CStreamRowset 類別

用於 `CCommand` 或 `CTable` 宣告中。

## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
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
|[CStreamRowset](#cstreamrowset)|建構函式。 具現化並初始化 `CStreamRowset` 物件。|
|[關閉](#close)|釋放類別中的[ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85))介面指標。|

## <a name="remarks"></a>備註

在您的 `CCommand` 或 `CTable` 宣告中使用 `CStreamRowset`，例如：

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

或

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` 會傳回 `ISequentialStream` 指標，它會儲存在 `m_spStream`中。 然後，您可以使用 `Read` 方法，以 XML 格式抓取（Unicode 字串）資料。 例如：

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 會執行 XML 格式設定，並將資料列集的所有資料行和所有資料列當做一個 XML 字串傳回。

> [!NOTE]
>  這項功能僅適用于 SQL Server 2000。

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset：： CStreamRowset

具現化並初始化 `CStreamRowset` 物件。

### <a name="syntax"></a>語法

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset：： Close

釋放類別中的[ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85))介面指標。

### <a name="syntax"></a>語法

```cpp
void Close();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
