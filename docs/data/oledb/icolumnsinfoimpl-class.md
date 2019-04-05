---
title: IColumnsInfoImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
ms.openlocfilehash: d9fbe95f87cfdf51ae9c52c7890e6f6c4075c89a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039789"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl 類別

提供實作[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))介面。

## <a name="syntax"></a>語法

```cpp
template <class T>
class ATL_NO_VTABLE IColumnsInfoImpl :
   public IColumnsInfo, 
   public CDBIDOps
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`IColumnsInfoImpl`。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[GetColumnInfo](#getcolumninfo)|傳回大部分消費者所需的資料行中繼資料。|
|[MapColumnIDs](#mapcolumnids)|在指定的資料行識別碼所識別的資料列集傳回的資料行序數的陣列。|

## <a name="remarks"></a>備註

在 資料列集和命令上必要的介面。 若要修改您的提供者的行為`IColumnsInfo`實作中，您需要修改提供者資料行對應。

## <a name="getcolumninfo"></a> IColumnsInfoImpl::GetColumnInfo

傳回大部分消費者所需的資料行中繼資料。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,
   DBCOLUMNINFO** prgInfo,
   OLECHAR** ppStringsBuffer);
```

#### <a name="parameters"></a>參數

請參閱[icolumnsinfo:: Getcolumninfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中*OLE DB 程式設計人員參考*。

## <a name="mapcolumnids"></a> IColumnsInfoImpl::MapColumnIDs

在指定的資料行識別碼所識別的資料列集傳回的資料行序數的陣列。

### <a name="syntax"></a>語法

```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,
   const DBID rgColumnIDs[],
   DBORDINAL rgColumns[]);
```

#### <a name="parameters"></a>參數

請參閱[IColumnsInfo::MapColumnIDs](/previous-versions/windows/desktop/ms714200(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)