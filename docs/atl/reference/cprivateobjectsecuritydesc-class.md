---
title: C私有物件安全德斯類
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
ms.openlocfilehash: 2fcfdfecab649b571047613ec0889b02d2c7a7a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331408"
---
# <a name="cprivateobjectsecuritydesc-class"></a>C私有物件安全德斯類

此類表示私有物件安全描述符物件。

## <a name="syntax"></a>語法

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C私有物件安全資料::C私有物件安全數據](#cprivateobjectsecuritydesc)|建構函式。|
|[C 私有物件安全資料:*C 私有物件安全資料c](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C私有物件安全資料::轉換為自動繼承](#converttoautoinherit)|呼叫此方法可將安全描述符及其存取控制列表 (ACL) 轉換為支援自動傳播可繼承的存取控制項目 (ACEs) 的格式。|
|[C 私有物件安全::建立](#create)|呼叫此方法以為調用資源管理器創建的私有物件分配和初始化自我相關安全描述符。|
|[C 私有物件安全:取得](#get)|呼叫此方法從私有物件的安全描述符中檢索資訊。|
|[C 私有物件安全::設定](#set)|呼叫此方法以修改私有物件的安全描述符。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算符 |](#operator_eq)|指派運算子。|

## <a name="remarks"></a>備註

此類派生自[CSecurityDesc,](../../atl/reference/csecuritydesc-class.md)它提供了建立和管理私有物件的安全描述符的方法。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>C私有物件安全資料::轉換為自動繼承

呼叫此方法可將安全描述符及其存取控制列表 (ACL) 轉換為支援自動傳播可繼承的存取控制項目 (ACEs) 的格式。

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>參數

*pParent*<br/>
指向引用該物件的父容器的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標。 如果沒有父容器,則此參數為 NULL。

*ObjectType*<br/>
指向標識與`GUID`當前物件關聯的物件類型的結構的指標。 如果物件沒有 GUID,則將*物件類型*設定為 NULL。

*bIsDirectory 物件*<br/>
指定新物件是否可以包含其他物件。 值為 true 表示新對像是容器。 false 值表示新物件不是容器。

*通用對應*<br/>
指向[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)結構的指標,該結構指定從每個泛型許可權映射到物件的特定許可權。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

此方法嘗試確定當前安全描述符的可自由存取控制列表 (DACL) 和系統存取控制列表 (SACL) 中的 ACE 是否從父安全描述符繼承。 它調用[Convert 到自動繼承私有物件安全](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)功能。

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>C私有物件安全資料::C私有物件安全數據

建構函式。

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>備註

初始化 `CPrivateObjectSecurityDesc` 物件。

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>C 私有物件安全資料:*C 私有物件安全資料c

解構函式。

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>備註

析構函數釋放所有分配的資源,並刪除私有物件的安全描述符。

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a>C 私有物件安全::建立

呼叫此方法以為調用資源管理器創建的私有物件分配和初始化自我相關安全描述符。

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
指向引用正在其中創建新物件的父目錄的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標。 如果沒有父目錄,則設置為 NULL。

*pCreator*<br/>
指向物件創建者提供的安全描述符的指標。 如果物件的建立者未顯式傳遞新物件的安全資訊,則將此參數設置為 NULL。

*bIsDirectory 物件*<br/>
指定新物件是否可以包含其他物件。 值為 true 表示新對像是容器。 false 值表示新物件不是容器。

*權杖*<br/>
引用為其創建該物件的用戶端進程的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件。

*通用對應*<br/>
指向[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)結構的指標,該結構指定從每個泛型許可權映射到物件的特定許可權。

*ObjectType*<br/>
指向標識與`GUID`當前物件關聯的物件類型的結構的指標。 如果物件沒有 GUID,則將*物件類型*設定為 NULL。

*bIs容器物件*<br/>
指定新物件是否可以包含其他物件。 值為 true 表示新對像是容器。 false 值表示新物件不是容器。

*自動繼承標誌*<br/>
一組位標誌,用於控制如何從*pParent*繼承存取控制項目 (ACE)。 有關詳細資訊[,請參閱創建私有物件安全Ex。](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

此方法呼叫[建立私有物件異常或](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity)[建立私有物件安全Ex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)。

第二種方法允許指定新物件的物件類型 GUID 或控制 AES 的繼承方式。

> [!NOTE]
> 自我相對安全描述符是一種安全描述符,用於將其所有安全資訊存儲在連續記憶體塊中。

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a>C 私有物件安全:取得

呼叫此方法從私有物件的安全描述符中檢索資訊。

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>參數

*si*<br/>
一組位標誌,指示要檢索的安全描述符的各個部分。 此值可以是[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)位標誌的組合。

*pResult*<br/>
指向從指定安全描述符接收請求資訊副本的[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標。

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

安全描述符是一個結構和關聯數據,其中包含可保護物件的安全資訊。

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>C 私有物件安全數據::運算符 |

指派運算子。

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>參數

*rhs*<br/>
要指派給目前物件的 `CPrivateObjectSecurityDesc` 物件。

### <a name="return-value"></a>傳回值

返回更新`CPrivateObjectSecurityDesc`的物件。

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a>C 私有物件安全::設定

呼叫此方法以修改私有物件的安全描述符。

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
一組位標誌,指示要設置的安全描述符的各個部分。 此值可以是[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)位標誌的組合。

*修改*<br/>
指向[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)物件的指標。 *si*參數指示的安全描述符部分將應用於物件的安全描述符。

*通用對應*<br/>
指向[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)結構的指標,該結構指定從每個泛型許可權映射到物件的特定許可權。

*權杖*<br/>
引用為其創建該物件的用戶端進程的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件。

*自動繼承標誌*<br/>
一組位標誌,用於控制如何從*pParent*繼承存取控制項目 (ACE)。 有關詳細資訊[,請參閱創建私有物件安全Ex。](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)

### <a name="return-value"></a>傳回值

如果成功則傳回 true，失敗則傳回 false。

### <a name="remarks"></a>備註

第二種方法允許指定物件的物件類型 GUID 或控制 AES 的繼承方式。

## <a name="see-also"></a>另請參閱

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc 類別](../../atl/reference/csecuritydesc-class.md)
