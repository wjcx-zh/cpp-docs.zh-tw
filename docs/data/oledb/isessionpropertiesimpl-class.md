---
title: ISessionPropertiesImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- ISessionPropertiesImpl.SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: 57a94ccd8ee3871742e9c8360c56381f85053380
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844830"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 類別

提供 [ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85)) 介面的實作為。

## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的類別 `ISessionPropertiesImpl` 。

*PropClass*<br/>
使用者可定義的屬性類別，預設為 *T*。

## <a name="requirements"></a>規格需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[GetProperties](#getproperties)|傳回會話屬性群組中目前在會話上設定的屬性清單。|
|[SetProperties](#setproperties)|設定會話屬性群組中的屬性。|

## <a name="remarks"></a>備註

會話上的強制介面。 這個類別會藉由呼叫 [屬性集對應](../../data/oledb/begin-propset-map.md)所定義的靜態函式，來實作為會話屬性。 您應在您的 session 類別中指定屬性集對應。

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a> ISessionPropertiesImpl：： GetProperties

傳回 `DBPROPSET_SESSION` 目前在會話上設定之屬性群組中的屬性清單。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ISessionProperties：： GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) 。

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a> ISessionPropertiesImpl：： SetProperties

設定屬性群組中的屬性 `DBPROPSET_SESSION` 。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ISessionProperties：： SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
