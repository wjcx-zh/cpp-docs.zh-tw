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
ms.openlocfilehash: c1a3539ea4ea705ad8bd1e40acda965ef66e2051
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077719"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl 類別

提供[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))介面的執行。

## <a name="syntax"></a>語法

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自 `ISessionPropertiesImpl`的類別。

*PropClass*<br/>
使用者可定義的屬性類別，預設為*T*。

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[GetProperties](#getproperties)|傳回會話中目前設定的會話屬性群組中的屬性清單。|
|[SetProperties](#setproperties)|設定會話屬性群組中的屬性。|

## <a name="remarks"></a>備註

會話上的強制介面。 這個類別會藉由呼叫[屬性集對應](../../data/oledb/begin-propset-map.md)所定義的靜態函式，來實作用會話屬性。 您應該在會話類別中指定屬性集對應。

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a>ISessionPropertiesImpl：： GetProperties

傳回目前在會話上設定的 `DBPROPSET_SESSION` 屬性群組中的屬性清單。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ISessionProperties：： GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) 。

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a>ISessionPropertiesImpl：： SetProperties

設定 `DBPROPSET_SESSION` 屬性群組中的屬性。

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