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
ms.openlocfilehash: 165f7124657cbaf0c0f94171eaf9394011796aea
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447046"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl 類別

提供[ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85))介面的執行。

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

## <a name="requirements"></a>需求

**Header:** atldb.h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

|||
|-|-|
|[GetProperties](#getproperties)|傳回資料列集屬性群組中，目前要求之資料列集的屬性清單。|
|[SetProperties](#setproperties)|設定資料列集屬性群組中的屬性。|

## <a name="remarks"></a>備註

這在命令上是必要的。 執行是由[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)宏所定義的靜態函式所提供。

## <a name="getproperties"></a>ICommandPropertiesImpl：： GetProperties

使用命令的屬性對應傳回所有要求的屬性集。

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

## <a name="setproperties"></a>ICommandPropertiesImpl：： SetProperties

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