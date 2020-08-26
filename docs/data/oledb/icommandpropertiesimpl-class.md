---
title: ICommandPropertiesImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: f71ca7f5fb675916c9db7e5720e6c148f2131351
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845571"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 類別

提供 [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) 介面的實作為。

## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自

*PropClass*<br/>
您的屬性類別。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[GetProperties](#getproperties)|傳回資料列集屬性群組中目前針對資料列集所要求的屬性清單。|
|[SetProperties](#setproperties)|設定資料列集屬性群組中的屬性。|

## <a name="remarks"></a>備註

這是命令的必要項。 此實作為由 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) 巨集定義的靜態函式所提供。

## <a name="icommandpropertiesimplgetproperties"></a><a name="getproperties"></a> ICommandPropertiesImpl：： GetProperties

使用命令的屬性對應，傳回所有要求的屬性集。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ICommandProperties：： GetProperties](/previous-versions/windows/desktop/ms723119(v=vs.85)) 。

### <a name="remarks"></a>備註

請參閱 [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)。

## <a name="icommandpropertiesimplsetproperties"></a><a name="setproperties"></a> ICommandPropertiesImpl：： SetProperties

設定命令物件的屬性。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ICommandProperties：： SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
