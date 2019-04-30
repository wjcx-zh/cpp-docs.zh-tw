---
title: ISessionPropertiesImpl 類別
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- GetProperties
- ISessionPropertiesImpl.SetProperties
- SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: ed8b7a271bc6ac234fc9276d6c88d26848da24f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390681"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 類別

提供實作[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))介面。

## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`ISessionPropertiesImpl`。

*PropClass*<br/>
使用者可定義屬性類別，預設值為*T*。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[GetProperties](#getproperties)|傳回目前所設定的工作階段的工作階段屬性群組中的屬性清單。|
|[SetProperties](#setproperties)|設定工作階段屬性群組中的屬性。|

## <a name="remarks"></a>備註

在 工作階段上必要的介面。 這個類別會實作藉由呼叫靜態函式所定義的工作階段屬性[屬性集對應](../../data/oledb/begin-propset-map.md)。 在您的工作階段類別，應該指定屬性集對應。

## <a name="getproperties"></a> Isessionpropertiesimpl:: Getproperties

傳回清單中的屬性`DBPROPSET_SESSION`目前所設定的工作階段的屬性群組。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>參數

請參閱[ISessionProperties::GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="setproperties"></a> Isessionpropertiesimpl:: Setproperties

在 設定屬性`DBPROPSET_SESSION`屬性群組。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>參數

請參閱[ISessionProperties::SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85))中*OLE DB 程式設計人員參考*。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)