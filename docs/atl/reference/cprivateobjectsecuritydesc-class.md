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
ms.openlocfilehash: f62d289418280a05f390bf9cdec23ea30632aed2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833500"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc 類別

此類別代表私用物件安全描述項物件。

## <a name="syntax"></a>語法

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|建構函式。|
|[CPrivateObjectSecurityDesc：： ~ CPrivateObjectSecurityDesc](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|呼叫這個方法，將安全描述項及其存取控制清單 (Acl) 為支援自動傳播可繼承的存取控制專案 (Ace) 的格式。|
|[CPrivateObjectSecurityDesc：： Create](#create)|呼叫這個方法來配置和初始化由呼叫資源管理員所建立之私用物件的自我相關安全描述項。|
|[CPrivateObjectSecurityDesc：： Get](#get)|呼叫這個方法，以從私用物件的安全描述項取出資訊。|
|[CPrivateObjectSecurityDesc：： Set](#set)|呼叫這個方法來修改私用物件的安全描述項。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[運算子 =](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

這個衍生自 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md)的類別提供了建立和管理私用物件安全描述項的方法。

如需 Windows 中存取控制模型的簡介，請參閱 Windows SDK 中的 [存取控制](/windows/win32/SecAuthZ/access-control) 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>規格需求

**標頭：** atlsecurity.h。h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a> CPrivateObjectSecurityDesc::ConvertToAutoInherit

呼叫這個方法，將安全描述項及其存取控制清單 (Acl) 為支援自動傳播可繼承的存取控制專案 (Ace) 的格式。

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>參數

*pParent*<br/>
參考物件父容器之 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) 物件的指標。 如果沒有父容器，此參數為 Null。

*ObjectType*<br/>
`GUID`結構的指標，此結構會識別與目前物件相關聯的物件類型。 如果物件沒有 GUID，請將 *ObjectType* 設定為 Null。

*bIsDirectoryObject*<br/>
指定新的物件是否可以包含其他物件。 值為 true 表示新物件為容器。 值為 false 表示新的物件不是容器。

*GenericMapping*<br/>
[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)結構的指標，指定從每個泛型許可權到物件之特定許可權的對應。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

這個方法會嘗試判斷任意存取控制清單中的 Ace (DACL) 和目前安全描述項的系統存取控制清單 (SACL) 是否繼承自父安全描述項。 它會呼叫 [ConvertToAutoInheritPrivateObjectSecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) 函數。

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a> CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

建構函式。

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>備註

初始化 `CPrivateObjectSecurityDesc` 物件。

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a> CPrivateObjectSecurityDesc：： ~ CPrivateObjectSecurityDesc

解構函式。

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>備註

此函式會釋出所有已配置的資源，並刪除私用物件的安全描述項。

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a> CPrivateObjectSecurityDesc：： Create

呼叫這個方法來配置和初始化由呼叫資源管理員所建立之私用物件的自我相關安全描述項。

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
參考在其中建立新物件之父目錄的 [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) 物件指標。 如果沒有上層目錄，則設定為 Null。

*pCreator*<br/>
物件建立者所提供之安全描述項的指標。 如果物件的建立者未明確傳遞新物件的安全性資訊，請將此參數設定為 Null。

*bIsDirectoryObject*<br/>
指定新的物件是否可以包含其他物件。 值為 true 表示新物件為容器。 值為 false 表示新的物件不是容器。

*權杖*<br/>
要在其上建立物件之用戶端進程的 [CAccessToken](../../atl/reference/caccesstoken-class.md) 物件參考。

*GenericMapping*<br/>
[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)結構的指標，指定從每個泛型許可權到物件之特定許可權的對應。

*ObjectType*<br/>
`GUID`結構的指標，此結構會識別與目前物件相關聯的物件類型。 如果物件沒有 GUID，請將 *ObjectType* 設定為 Null。

*bIsContainerObject*<br/>
指定新的物件是否可以包含其他物件。 值為 true 表示新物件為容器。 值為 false 表示新的物件不是容器。

*AutoInheritFlags*<br/>
一組位旗標，可控制如何從 *pParent*繼承 (ace) 的存取控制專案。 如需詳細資訊，請參閱 [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

這個方法會呼叫 [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) 或 [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)。

第二種方法允許指定新物件的物件類型 GUID，或控制如何繼承 Ace。

> [!NOTE]
> 自我相關的安全描述項是安全描述項，可將它的所有安全性資訊儲存在連續的記憶體區塊中。

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a> CPrivateObjectSecurityDesc：： Get

呼叫這個方法，以從私用物件的安全描述項取出資訊。

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>參數

*四*<br/>
一組位旗標，表示要取出的安全描述項部分。 這個值可以是 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) 位旗標的組合。

*pResult*<br/>
[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標，該物件會從指定的安全描述項接收所要求資訊的複本。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

安全描述項是包含安全物件安全性資訊的結構和相關聯的資料。

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a> CPrivateObjectSecurityDesc：： operator =

指派運算子。

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要指派給目前物件的 `CPrivateObjectSecurityDesc` 物件。

### <a name="return-value"></a>傳回值

傳回更新的 `CPrivateObjectSecurityDesc` 物件。

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a> CPrivateObjectSecurityDesc：： Set

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

*四*<br/>
一組位旗標，表示要設定的安全描述項部分。 這個值可以是 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) 位旗標的組合。

*修改*<br/>
[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標。 由 *si* 參數表示之安全描述項的部分會套用至物件的安全描述項。

*GenericMapping*<br/>
[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)結構的指標，指定從每個泛型許可權到物件之特定許可權的對應。

*權杖*<br/>
要在其上建立物件之用戶端進程的 [CAccessToken](../../atl/reference/caccesstoken-class.md) 物件參考。

*AutoInheritFlags*<br/>
一組位旗標，可控制如何從 *pParent*繼承 (ace) 的存取控制專案。 如需詳細資訊，請參閱 [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

第二種方法允許指定物件的物件類型 GUID，或控制如何繼承 Ace。

## <a name="see-also"></a>另請參閱

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc 類別](../../atl/reference/csecuritydesc-class.md)
