---
title: CComCritSeclock 類別
ms.date: 11/04/2016
f1_keywords:
- CComCritSecLock
- ATLBASE/ATL::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::CComCritSecLock
- ATLBASE/ATL::CComCritSecLock::Lock
- ATLBASE/ATL::CComCritSecLock::Unlock
helpviewer_keywords:
- CComCritSecLock class
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
ms.openlocfilehash: 4b2ef093c1142b592ad2a6605a08bd8c34a643ea
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748068"
---
# <a name="ccomcritseclock-class"></a>CComCritSeclock 類別

此類提供鎖定和解鎖關鍵截面物件的方法。

## <a name="syntax"></a>語法

```
template<class TLock> class CComCritSecLock
```

#### <a name="parameters"></a>參數

*TLock*<br/>
要鎖定和解鎖的物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComCritSecLock:CComCritSecLock](#ctor)|建構函式。|
|[CComCritSecLock:*CComCritSecLock](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComCritSecLock:鎖定](#lock)|調用此方法以鎖定關鍵截面物件。|
|[CComCritSecLock:解鎖](#unlock)|調用此方法以解鎖關鍵截面物件。|

## <a name="remarks"></a>備註

使用此類以比[CCom臨界節類](../../atl/reference/ccomcriticalsection-class.md)或[CComAuto 臨界節類](../../atl/reference/ccomautocriticalsection-class.md)更安全的方式鎖定和解鎖物件。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="ccomcritseclockccomcritseclock"></a><a name="ctor"></a>CComCritSecLock:CComCritSecLock

建構函式。

```
CComCritSecLock(TLock& cs, bool bInitialLock = true);
```

### <a name="parameters"></a>參數

*cs*<br/>
關鍵截面物件。

*b 初始鎖定*<br/>
初始鎖定狀態 **:true**表示鎖定。

### <a name="remarks"></a>備註

初始化關鍵截面物件。

## <a name="ccomcritseclockccomcritseclock"></a><a name="dtor"></a>CComCritSecLock:*CComCritSecLock

解構函式。

```
~CComCritSecLock() throw();
```

### <a name="remarks"></a>備註

解鎖關鍵截面物件。

## <a name="ccomcritseclocklock"></a><a name="lock"></a>CComCritSecLock:鎖定

調用此方法以鎖定關鍵截面物件。

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>傳回值

如果物件已成功鎖定,則返回S_OK,或者失敗時出現 HRESULT 錯誤。

### <a name="remarks"></a>備註

如果物件已鎖定,則調試生成中將發生 ASSERT 錯誤。

## <a name="ccomcritseclockunlock"></a><a name="unlock"></a>CComCritSecLock:解鎖

調用此方法以解鎖關鍵截面物件。

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>備註

如果物件已解鎖,則調試生成中將發生 ASSERT 錯誤。

## <a name="see-also"></a>另請參閱

[CCom臨界節類](../../atl/reference/ccomcriticalsection-class.md)<br/>
[CComAuto關鍵科類別](../../atl/reference/ccomautocriticalsection-class.md)
