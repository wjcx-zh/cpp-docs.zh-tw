---
title: CAutoRevertImpersonation 類別
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
ms.openlocfilehash: f1941bfcd7689ab9d22f5094af0eb833a84dab6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497677"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation 類別

這個類別會在[CAccessToken](../../atl/reference/caccesstoken-class.md)物件超出範圍時, 將其還原為 nonimpersonating 狀態。

## <a name="syntax"></a>語法

```
class CAutoRevertImpersonation
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|`CAutoRevertImpersonation`結構物件|
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|終結物件, 並還原存取權杖模擬。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAutoRevertImpersonation::Attach](#attach)|將存取權杖的模擬回復自動化。|
|[CAutoRevertImpersonation::Detach](#detach)|取消自動模擬回復。|
|[CAutoRevertImpersonation::GetAccessToken](#getaccesstoken)|抓取與此物件相關聯的目前存取權杖。|

## <a name="remarks"></a>備註

[存取權杖](/windows/win32/SecAuthZ/access-tokens)是一種物件, 可描述進程或執行緒的安全性內容, 並配置給每位登入 windows NT 或 windows 2000 系統的使用者。 這些存取權杖可以使用`CAccessToken`類別來表示。

有時必須模擬存取權杖。 這個類別是為了方便起見而提供, 但不會執行存取權杖的模擬;它只會對 nonimpersonated 狀態執行自動回復。 這是因為權杖存取模擬可以用數種不同的方式來執行。

如需 Windows 中的存取控制模型簡介, 請參閱 Windows SDK 中的[存取控制](/windows/win32/SecAuthZ/access-control)。

## <a name="requirements"></a>需求

**標頭:** atlsecurity。h

##  <a name="attach"></a>CAutoRevertImpersonation:: Attach

將存取權杖的模擬回復自動化。

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>參數

*pAT*<br/>
要自動還原之[CAccessToken](../../atl/reference/caccesstoken-class.md)物件的位址

### <a name="remarks"></a>備註

只有在使用 Null `CAccessToken`指標建立[CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)物件, 或先前已呼叫卸[離](#detach)時, 才應該使用這個方法。 在簡單的情況下, 不需要使用此方法。

##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

建構 `CAutoRevertImpersonation` 物件。

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>參數

*pAT*<br/>
要自動還原之[CAccessToken](../../atl/reference/caccesstoken-class.md)物件的位址。

### <a name="remarks"></a>備註

存取權杖的實際模擬應該與建立`CAutoRevertImpersonation`物件之前, 分別從和最好的執行。 當物件超出範圍時, `CAutoRevertImpersonation`將會自動還原此模擬。

##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

終結物件, 並還原存取權杖模擬。

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>備註

針對在結構上或透過[Attach](#attach)方法提供的[CAccessToken](../../atl/reference/caccesstoken-class.md)物件, 還原目前作用中的任何模擬。 如果沒有`CAccessToken`關聯, 則析構函式不會有任何作用。

##  <a name="detach"></a>CAutoRevertImpersonation::D etach

取消自動模擬回復。

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>傳回值

先前相關聯[CAccessToken](../../atl/reference/caccesstoken-class.md)的位址, 如果沒有關聯存在, 則為 Null。

### <a name="remarks"></a>備註

呼叫卸**離**可`CAutoRevertImpersonation`防止物件還原目前作用於與此物件相關聯之[CAccessToken](../../atl/reference/caccesstoken-class.md)物件的任何模擬。 `CAutoRevertImpersonation`然後可以使用 [[附加](#attach)] 來終結, 而不會影響或`CAccessToken`重新關聯至相同或另一個物件。

##  <a name="getaccesstoken"></a>CAutoRevertImpersonation:: GetAccessToken

抓取與此物件相關聯的目前存取權杖。

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>傳回值

先前相關聯[CAccessToken](../../atl/reference/caccesstoken-class.md)的位址, 如果沒有關聯存在, 則為 Null。

### <a name="remarks"></a>備註

如果針對包含`CAccessToken`物件模擬回復的目的來呼叫這個方法, 則應該改用卸[離](#detach)方法。

## <a name="see-also"></a>另請參閱

[ATLSecurity 範例](../../overview/visual-cpp-samples.md)<br/>
[存取權杖](/windows/win32/SecAuthZ/access-tokens)<br/>
[類別總覽](../../atl/atl-class-overview.md)
