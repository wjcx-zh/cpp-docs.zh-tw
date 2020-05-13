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
ms.openlocfilehash: ad4987422fd200faef141150908d4df0722f669a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366279"
---
# <a name="cstreamrowset-class"></a>CStreamRowset 類別

在`CCommand``CTable`或聲明中使用。

## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>參數

*TAccessor*<br/>
訪問器類。

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|建構函式。 實例化和初始化`CStreamRowset`物件。|
|[關閉](#close)|釋放類中的[I順序流](/previous-versions/windows/desktop/ms718035(v=vs.85))介面指標。|

## <a name="remarks"></a>備註

在`CStreamRowset``CCommand``CTable`您的 或 宣告中使用,例如:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

或

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute`返回存儲在`ISequentialStream`中的`m_spStream`指標。 然後,使用`Read`方法以 XML 格式檢索 (Unicode 字串) 資料。 例如：

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 執行 XML 格式,並將將行集的所有列和所有行作為一個 XML 字串返回。

> [!NOTE]
> 此功能僅適用於 SQL Server 2000。

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset:CStreamRowset

實例化和初始化`CStreamRowset`物件。

### <a name="syntax"></a>語法

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset:關閉

釋放類中的[I順序流](/previous-versions/windows/desktop/ms718035(v=vs.85))介面指標。

### <a name="syntax"></a>語法

```cpp
void Close();
```

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
