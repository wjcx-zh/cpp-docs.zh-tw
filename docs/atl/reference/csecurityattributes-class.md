---
title: 安全屬性類
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 113bcebb7461415590156206ee7aa4c91e0e93d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330979"
---
# <a name="csecurityattributes-class"></a>安全屬性類

此類是安全屬性結構的精簡包裝器。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[安全屬性::安全屬性](#csecurityattributes)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[安全屬性::設定](#set)|呼叫此方法以設定物件的屬性`CSecurityAttributes`。|

## <a name="remarks"></a>備註

結構`SECURITY_ATTRIBUTES`包含用於創建物件[的安全描述符](/windows/win32/api/winnt/ns-winnt-security_descriptor),並指定通過指定此結構檢索的句柄是否可繼承。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a>安全屬性::安全屬性

建構函式。

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>參數

*r 安全性描述器*<br/>
安全性描述元的參考。

*b繼承者*<br/>
指定是否在建立新處理序時繼承傳回的控制代碼。 如果此成員為 true，新處理序會繼承控制代碼。

## <a name="csecurityattributesset"></a><a name="set"></a>安全屬性::設定

呼叫此方法以設定物件的屬性`CSecurityAttributes`。

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>參數

*r 安全性描述器*<br/>
安全性描述元的參考。

*b繼承手柄*<br/>
指定是否在建立新處理序時繼承傳回的控制代碼。 如果此成員為 true，新處理序會繼承控制代碼。

### <a name="remarks"></a>備註

建構函數使用此方法來初始化`CSecurityAttributes`物件。

## <a name="see-also"></a>另請參閱

[安全範例](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[安全性描述項](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[類別概觀](../../atl/atl-class-overview.md)<br/>
[安全全域功能](../../atl/reference/security-global-functions.md)
