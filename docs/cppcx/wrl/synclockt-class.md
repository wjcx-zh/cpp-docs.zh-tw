---
title: SyncLockT 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 52c4404fa28f680a9a7a4592d03f535e8406d1a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374275"
---
# <a name="synclockt-class"></a>SyncLockT 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>參數

*同步特徵*<br/>
可以取得資源擁有權的類型。

## <a name="remarks"></a>備註

表示可以獲取資源的獨佔或共用擁有權的類型。

例如`SyncLockT`,該類用於幫助實現[SRWLock](srwlock-class.md)類。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                      | 描述
----------------------------------------- | ----------------------------------------------------
[同步鎖定T:同步鎖定](#synclockt)        | 將 `SyncLockT` 類別的新執行個體初始化。
[同步鎖定T:*同步鎖定](#tilde-synclockt) | 取消初始化類的`SyncLockT`實例。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                               | 描述
---------------------------------- | ----------------------------------------------------
[同步鎖定T:同步鎖定](#synclockt) | 將 `SyncLockT` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                             | 描述
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[同步鎖定T:鎖定](#islocked) | 指示當前物件是否`SyncLockT`擁有資源;如果當前物件是否擁有資源,則表明當前物件是否擁有資源。也就是說,`SyncLockT`物件已*鎖定*。
[同步鎖定T:解鎖](#unlock)     | 釋放對當前`SyncLockT`物件(如果有)持有的資源的控制。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                      | 描述
------------------------- | -------------------------------------------------------------------
[同步鎖定T:sync_](#sync) | 保存類`SyncLockT`表示的基礎資源。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SyncLockT`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::D

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>同步鎖定T:*同步鎖定

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
~SyncLockT();
```

### <a name="remarks"></a>備註

取消初始化類的`SyncLockT`實例。

此析構函數還會解鎖當前`SyncLockT`實例。

## <a name="synclocktislocked"></a><a name="islocked"></a>同步鎖定T:鎖定

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>傳回值

如果物件已`SyncLockT`鎖定,**則為 true;** 否則,**假**。

### <a name="remarks"></a>備註

指示當前物件是否`SyncLockT`擁有資源;如果當前物件是否擁有資源,則表明當前物件是否擁有資源。也就是說,`SyncLockT`物件已*鎖定*。

## <a name="synclocktsync_"></a><a name="sync"></a>同步鎖定T:sync_

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>備註

保存類`SyncLockT`表示的基礎資源。

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>同步鎖定T:同步鎖定

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>參數

*其他*<br/>
對另一個`SyncLockT`物件的 rvalue 引用。

*sync*<br/>
對另一個`SyncLockWithStatusT`物件的引用。

### <a name="remarks"></a>備註

將 `SyncLockT` 類別的新執行個體初始化。

第一個建構函數從參數*其他*`SyncLockT`指定的`SyncLockT`另一 個物件初始化當前物件,然後`SyncLockT`使另一個 物件無效。 第二個構造函數`protected`是 ,`SyncLockT`並將當前 物件初始化為無效狀態。

## <a name="synclocktunlock"></a><a name="unlock"></a>同步鎖定T:解鎖

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
void Unlock();
```

### <a name="remarks"></a>備註

釋放對當前`SyncLockT`物件(如果有)持有的資源的控制。
