---
title: ITopologyExecutionResource 結構
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 4bfb614d5ffd6a399fae33d38a50cee62f17c208
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339505"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 結構

資源管理員所定義的執行資源介面。

## <a name="syntax"></a>語法

```
struct ITopologyExecutionResource;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ITopologyExecutionResource::GetId](#getid)|傳回這個執行資源的資源管理員唯一識別項。|
|[ITopologyExecutionResource::GetNext](#getnext)|讓介面返回列舉順序中的下一個執行資源。|

## <a name="remarks"></a>備註

此介面通常用於為觀察資源管理員逐步系統的拓撲。

## <a name="inheritance-hierarchy"></a>繼承階層

`ITopologyExecutionResource`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="getid"></a>  Itopologyexecutionresource:: Getid 方法

傳回這個執行資源的資源管理員唯一識別項。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

這個執行資源的資源管理員唯一識別項。

##  <a name="getnext"></a>  Itopologyexecutionresource:: Getnext 方法

讓介面返回列舉順序中的下一個執行資源。

```
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>傳回值

介面返回列舉順序中的下一個執行資源。 如果節點的列舉順序中沒有這個執行資源所屬的其他節點，這個方法將傳回值 `NULL`。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
