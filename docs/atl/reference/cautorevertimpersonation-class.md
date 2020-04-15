---
title: C 自動回復模擬類別
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: 813b6f0dd33bdfa85476b816086217a7892f4476
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318784"
---
# <a name="cautorevertimpersonation-class"></a>C 自動回復模擬類別

此類將[CAccessToken](../../atl/reference/caccesstoken-class.md)物件還原為非模擬狀態,當它超出範圍時。

## <a name="syntax"></a>語法

```
class CAutoRevertImpersonation
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 自動回復模擬::C 自動回復模擬](#cautorevertimpersonation)|建構`CAutoRevertImpersonation`物件|
|[C自動還原模擬::_C 自動還原類比](#dtor)|銷毀物件並還原訪問令牌類比。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 自動回復模擬:附加](#attach)|自動模擬訪問權杖的重新回歸。|
|[C 自動回復模擬::D](#detach)|取消自動類比還原。|
|[C 自動回復模擬::取得存取權杖](#getaccesstoken)|檢索與此物件關聯的訪問權杖電流。|

## <a name="remarks"></a>備註

[訪問權杖](/windows/win32/SecAuthZ/access-tokens)是描述進程或線程的安全上下文的物件,並分配給登錄到 Windows NT 或 Windows 2000 系統的每個使用者。 這些訪問令牌可以隨`CAccessToken`類一起表示。

有時需要模擬訪問權杖。 此類是為方便起見提供的,但它不執行訪問令牌的類比;因此,它無法執行訪問權杖的類比。它僅執行自動還原到非模擬狀態。 這是因為令牌訪問類比可以執行幾種不同的方式。

有關 Windows 中存取控制模型的簡介,請參閱 Windows SDK[中的存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標題:** atlsecurity.h

## <a name="cautorevertimpersonationattach"></a><a name="attach"></a>C 自動回復模擬:附加

自動模擬訪問權杖的重新回歸。

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>參數

*派特*<br/>
要自動回復的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件的位址

### <a name="remarks"></a>備註

僅當使用 NULL`CAccessToken`指標建立[CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)物件,或者以前呼叫[Detach](#detach)時,才應使用此方法。 對於簡單情況,不需要使用此方法。

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="cautorevertimpersonation"></a>C 自動回復模擬::C 自動回復模擬

建構 `CAutoRevertImpersonation` 物件。

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>參數

*派特*<br/>
要自動還原的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件的位址。

### <a name="remarks"></a>備註

存取權碼的實際模擬應與建立物件分開執行,最好是在建立物件之前`CAutoRevertImpersonation`執行 。 當物件超出範圍時,`CAutoRevertImpersonation`此模擬將自動還原。

## <a name="cautorevertimpersonationcautorevertimpersonation"></a><a name="dtor"></a>C自動還原模擬::_C 自動還原類比

銷毀物件並還原訪問令牌類比。

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>備註

還原當前在建構或透過[Attach](#attach)方法提供的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件當前有效的任何類比。 如果未`CAccessToken`關聯,則析構函數不起作用。

## <a name="cautorevertimpersonationdetach"></a><a name="detach"></a>C 自動回復模擬::D

取消自動類比還原。

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>傳回值

以前關聯的[CAccessToken](../../atl/reference/caccesstoken-class.md)的位址 ,如果不存在關聯,則為 NULL。

### <a name="remarks"></a>備註

調用**分離**`CAutoRevertImpersonation`可防止 物件還原當前與此物件關聯的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件生效的任何類比。 `CAutoRevertImpersonation`然後,可以使用[Attach](#attach)銷毀,但不起作用或重新關聯`CAccessToken`到同 一物件或其他物件。

## <a name="cautorevertimpersonationgetaccesstoken"></a><a name="getaccesstoken"></a>C 自動回復模擬::取得存取權杖

檢索與此物件關聯的訪問權杖電流。

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>傳回值

以前關聯的[CAccessToken](../../atl/reference/caccesstoken-class.md)的位址 ,如果不存在關聯,則為 NULL。

### <a name="remarks"></a>備註

如果為包含重新還原`CAccessToken`物件類比的目的調用此方法,則應改用[Detach](#detach)方法。

## <a name="see-also"></a>另請參閱

[ATL 安全範例](../../overview/visual-cpp-samples.md)<br/>
[存取權杖](/windows/win32/SecAuthZ/access-tokens)<br/>
[類別概觀](../../atl/atl-class-overview.md)
