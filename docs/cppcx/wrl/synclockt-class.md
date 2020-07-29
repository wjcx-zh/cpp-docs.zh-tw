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
ms.openlocfilehash: 6a6e176020624f02e778ba5684a374abfbafa9e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184666"
---
# <a name="synclockt-class"></a>SyncLockT 類別

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>參數

*SyncTraits*<br/>
可取得資源擁有權的類型。

## <a name="remarks"></a>備註

表示可取得資源之獨佔或共用擁有權的類型。

`SyncLockT`例如，會使用類別來協助執行[SRWLock](srwlock-class.md)類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                      | 說明
----------------------------------------- | ----------------------------------------------------
[SyncLockT：： SyncLockT](#synclockt)        | 初始化 `SyncLockT` 類別的新執行個體。
[SyncLockT：： ~ SyncLockT](#tilde-synclockt) | 將類別的實例 `SyncLockT` 。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                               | 說明
---------------------------------- | ----------------------------------------------------
[SyncLockT：： SyncLockT](#synclockt) | 初始化 `SyncLockT` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                             | 說明
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT：： IsLocked](#islocked) | 指出目前的物件是否擁有資源，亦即 `SyncLockT` `SyncLockT` 物件是否已*鎖定*。
[SyncLockT：： Unlock](#unlock)     | 釋放目前物件所持有之資源的控制權 `SyncLockT` （如果有的話）。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                      | 說明
------------------------- | -------------------------------------------------------------------
[SyncLockT：： sync_](#sync) | 保存類別所代表的基礎資源 `SyncLockT` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SyncLockT`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式：:D etails

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLockT：： ~ SyncLockT

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
~SyncLockT();
```

### <a name="remarks"></a>備註

將類別的實例 `SyncLockT` 。

這個析構函式也會解除鎖定目前的 `SyncLockT` 實例。

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLockT：： IsLocked

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>傳回值

**`true`** 如果 `SyncLockT` 物件已鎖定，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

指出目前的物件是否擁有資源，亦即 `SyncLockT` `SyncLockT` 物件是否已*鎖定*。

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLockT：： sync_

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>備註

保存類別所代表的基礎資源 `SyncLockT` 。

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLockT：： SyncLockT

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個物件的右值參考 `SyncLockT` 。

*保持*<br/>
另一個物件的參考 `SyncLockWithStatusT` 。

### <a name="remarks"></a>備註

初始化 `SyncLockT` 類別的新執行個體。

第一個函式會 `SyncLockT` 從其他參數指定的另一個物件初始化目前的物件 `SyncLockT` ，然後使另一個物件失效*other* `SyncLockT` 。 第二個函式是，會將 **`protected`** 目前的 `SyncLockT` 物件初始化為不正確狀態。

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLockT：： Unlock

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
void Unlock();
```

### <a name="remarks"></a>備註

釋放目前物件所持有之資源的控制權 `SyncLockT` （如果有的話）。
