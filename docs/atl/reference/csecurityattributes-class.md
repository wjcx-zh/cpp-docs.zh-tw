---
title: CSecurityAttributes 類別
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: b26de7a2a3426ed2fe86bd7ef50f6c5410fa5364
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503200"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 類別

這個類別是安全性屬性結構的精簡型包裝函式。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|呼叫這個方法來設定的屬性`CSecurityAttributes`物件。|

## <a name="remarks"></a>備註

`SECURITY_ATTRIBUTES`結構包含[安全性描述元](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)用於建立物件，並指定是否可繼承控制代碼藉由指定此結構擷取。

在 Windows 中的存取控制模型的簡介，請參閱 <<c0> [ 存取控制](/windows/desktop/SecAuthZ/access-control)Windows SDK 中。

## <a name="inheritance-hierarchy"></a>繼承階層

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>需求

**標頭：** atlsecurity.h

##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes

建構函式。

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>參數

*rSecurityDescriptor*<br/>
安全性描述元的參考。

*bInheritsHandle*<br/>
指定是否在建立新處理序時繼承傳回的控制代碼。 如果此成員為 true，新處理序會繼承控制代碼。

##  <a name="set"></a>  CSecurityAttributes::Set

呼叫這個方法來設定的屬性`CSecurityAttributes`物件。

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>參數

*rSecurityDescriptor*<br/>
安全性描述元的參考。

*bInheritHandle*<br/>
指定是否在建立新處理序時繼承傳回的控制代碼。 如果此成員為 true，新處理序會繼承控制代碼。

### <a name="remarks"></a>備註

這個方法建構函式用來初始化`CSecurityAttributes`物件。

## <a name="see-also"></a>另請參閱

[安全性範例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[安全性描述元](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全性全域函式](../../atl/reference/security-global-functions.md)
