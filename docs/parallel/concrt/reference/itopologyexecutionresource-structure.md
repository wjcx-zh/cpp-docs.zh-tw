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
ms.openlocfilehash: 2c9221cab1ac2d48bd099a769188e4bee797823c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368139"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 結構

資源管理員所定義的執行資源介面。

## <a name="syntax"></a>語法

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I拓撲執行資源:GetId](#getid)|傳回這個執行資源的資源管理員唯一識別項。|
|[I拓撲執行資源:取得下一個](#getnext)|讓介面返回列舉順序中的下一個執行資源。|

## <a name="remarks"></a>備註

此介面通常用於遍歷資源管理器觀察到的系統拓撲。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ITopologyExecutionResource`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="itopologyexecutionresourcegetid-method"></a><a name="getid"></a>I拓撲執行資源:GetId 方法

傳回這個執行資源的資源管理員唯一識別項。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

這個執行資源的資源管理員唯一識別項。

## <a name="itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a>I拓撲執行資源::獲取下一個方法

讓介面返回列舉順序中的下一個執行資源。

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>傳回值

介面返回列舉順序中的下一個執行資源。 如果節點的列舉順序中沒有這個執行資源所屬的其他節點，這個方法將傳回值 `NULL`。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
