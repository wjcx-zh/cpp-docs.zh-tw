---
title: CPrivateObjectSecurityDesc 類別
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: c1ac15d4d8254107a66e577321edb3c40578f240
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915799"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 類別

此類別代表私用物件安全描述項物件。

## <a name="syntax"></a>語法

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|建構函式。|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|呼叫這個方法, 將安全描述項和其存取控制清單 (Acl) 轉換成支援自動傳播可繼承存取控制專案 (Ace) 的格式。|
|[CPrivateObjectSecurityDesc::Create](#create)|呼叫這個方法, 為呼叫資源管理員所建立的私用物件配置及初始化自我關聯的安全描述項。|
|[CPrivateObjectSecurityDesc::Get](#get)|呼叫這個方法, 以從私用物件的安全描述項取得資訊。|
|[CPrivateObjectSecurityDesc::Set](#set)|呼叫這個方法來修改私用物件的安全描述項。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

這個類別衍生自[CSecurityDesc](../../atl/reference/csecuritydesc-class.md), 提供建立和管理私用物件安全描述項的方法。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/desktop/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

呼叫這個方法, 將安全描述項和其存取控制清單 (Acl) 轉換成支援自動傳播可繼承存取控制專案 (Ace) 的格式。

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>參數

*pParent*<br/>
參考物件之父容器的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件指標。 如果沒有父容器, 則此參數為 Null。

*ObjectType*<br/>
`GUID`結構的指標, 識別與目前物件相關聯的物件類型。 如果物件沒有 GUID, 請將*ObjectType*設定為 Null。

*bIsDirectoryObject*<br/>
指定新的物件是否可以包含其他物件。 值為 true 時, 表示新的物件是容器。 值為 false 時, 表示新的物件不是容器。

*GenericMapping*<br/>
[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-generic_mapping)結構的指標, 指定從每個泛型許可權到物件之特定許可權的對應。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

這個方法會嘗試判斷目前安全描述項的任意存取控制清單 (DACL) 和系統存取控制清單 (SACL) 中的 Ace 是否繼承自父系安全描述項。 它會呼叫[ConvertToAutoInheritPrivateObjectSecurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)函數。

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

建構函式。

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>備註

初始化 `CPrivateObjectSecurityDesc` 物件。

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc

解構函式。

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>備註

此析構函式會釋放所有配置的資源, 並刪除私用物件的安全描述項。

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

呼叫這個方法, 為呼叫資源管理員所建立的私用物件配置及初始化自我關聯的安全描述項。

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>參數

*pParent*<br/>
參考要在其中建立新物件之父目錄的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件指標。 如果沒有上層目錄, 則設定為 Null。

*pCreator*<br/>
物件的建立者所提供之安全描述項的指標。 如果物件的建立者未明確地傳遞新物件的安全性資訊, 請將此參數設定為 Null。

*bIsDirectoryObject*<br/>
指定新的物件是否可以包含其他物件。 值為 true 時, 表示新的物件是容器。 值為 false 時, 表示新的物件不是容器。

*權杖*<br/>
代表建立物件之用戶端進程的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件參考。

*GenericMapping*<br/>
[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-generic_mapping)結構的指標, 指定從每個泛型許可權到物件之特定許可權的對應。

*ObjectType*<br/>
`GUID`結構的指標, 識別與目前物件相關聯的物件類型。 如果物件沒有 GUID, 請將*ObjectType*設定為 Null。

*bIsContainerObject*<br/>
指定新的物件是否可以包含其他物件。 值為 true 時, 表示新的物件是容器。 值為 false 時, 表示新的物件不是容器。

*AutoInheritFlags*<br/>
一組位旗標, 控制如何從*pParent*繼承存取控制專案 (ace)。 如需詳細資訊, 請參閱[CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

這個方法會呼叫[CreatePrivateObjectSercurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity)或[CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)。

第二種方法允許指定新物件的物件類型 GUID, 或控制 Ace 的繼承方式。

> [!NOTE]
>  自我關聯安全描述項是一個安全描述項, 可將其所有安全性資訊儲存在連續的記憶體區塊中。

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

呼叫這個方法, 以從私用物件的安全描述項取得資訊。

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>參數

*si*<br/>
一組位旗標, 指出要取得的安全描述項部分。 這個值可以是[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)位旗標的組合。

*pResult*<br/>
[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標, 它會從指定的安全描述項接收要求的資訊複本。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

安全描述項是一個結構和相關聯的資料, 其中包含安全物件的安全性資訊。

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

指派運算子。

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要`CPrivateObjectSecurityDesc`指派給目前物件的物件。

### <a name="return-value"></a>傳回值

傳回已更新`CPrivateObjectSecurityDesc`的物件。

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

呼叫這個方法來修改私用物件的安全描述項。

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>參數

*si*<br/>
一組位旗標, 指出要設定的安全描述項的各個部分。 這個值可以是[SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information)位旗標的組合。

*他人*<br/>
[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標。 *Si*參數所指示的此安全描述項的部分會套用至物件的安全描述項。

*GenericMapping*<br/>
[GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-generic_mapping)結構的指標, 指定從每個泛型許可權到物件之特定許可權的對應。

*權杖*<br/>
代表建立物件之用戶端進程的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件參考。

*AutoInheritFlags*<br/>
一組位旗標, 控制如何從*pParent*繼承存取控制專案 (ace)。 如需詳細資訊, 請參閱[CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

第二種方法允許指定物件的物件類型 GUID, 或控制 Ace 的繼承方式。

## <a name="see-also"></a>另請參閱

[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-security_descriptor)<br/>
[類別總覽](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc 類別](../../atl/reference/csecuritydesc-class.md)
