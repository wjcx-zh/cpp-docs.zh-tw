---
title: SyncLockWithStatusT 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT class
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT, constructor
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
ms.openlocfilehash: 4b7dbe8ae1648e4185a9eb1e1142df4a3869aa2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216540"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT 類別

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>參數

*SyncTraits*<br/>
可取得資源之獨佔或共用擁有權的類型。

## <a name="remarks"></a>備註

表示可取得資源之獨佔或共用擁有權的類型。

`SyncLockWithStatusT`類別是用來執行[Mutex](mutex-class.md)和[信號](semaphore-class.md)類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                             | 說明
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT：： SyncLockWithStatusT](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 類別的新執行個體。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                                                             | 說明
---------------------------------------------------------------- | --------------------------------------------------------------
[SyncLockWithStatusT：： SyncLockWithStatusT](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                         | 說明
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT：： GetStatus](#getstatus) | 抓取目前物件的等候狀態 `SyncLockWithStatusT` 。
[SyncLockWithStatusT：： IsLocked](#islocked)   | 指出目前的物件是否擁有資源，亦即 `SyncLockWithStatusT` `SyncLockWithStatusT` 物件是否已*鎖定*。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                    | 說明
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[SyncLockWithStatusT：： status_](#status) | 在以目前物件為基礎的物件上進行鎖定作業之後，保留基礎等候作業的結果 `SyncLockWithStatusT` 。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式：:D etails

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>SyncLockWithStatusT：： GetStatus

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>傳回值

以類別為基礎之物件上的等候作業結果 `SyncLockWithStatusT` ，例如[Mutex](mutex-class.md)或[信號](semaphore-class.md)。 零（0）表示等候作業傳回已發出信號的狀態;否則，就會發生另一種狀態，例如已過的超時值。

### <a name="remarks"></a>備註

抓取目前物件的等候狀態 `SyncLockWithStatusT` 。

GetStatus （）函數會抓取基礎[status_](#status)資料成員的值。 當以類別為基礎的物件 `SyncLockWithStatusT` 執行鎖定作業時，物件會先等候物件變成可供使用。 該等候作業的結果會儲存在 `status_` 資料成員中。 資料成員的可能值 `status_` 是等候作業的傳回值。 如需詳細資訊，請參閱函數的傳回值 [`WaitForSingleObjectEx`](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobjectex) 。

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>SyncLockWithStatusT：： IsLocked

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>備註

指出目前的物件是否擁有資源，亦即 `SyncLockWithStatusT` `SyncLockWithStatusT` 物件是否已*鎖定*。

### <a name="return-value"></a>傳回值

**`true`** 如果 `SyncLockWithStatusT` 物件已鎖定，則為，否則為 **`false`** 。

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>SyncLockWithStatusT：： status_

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
DWORD status_;
```

### <a name="remarks"></a>備註

在以目前物件為基礎的物件上進行鎖定作業之後，保留基礎等候作業的結果 `SyncLockWithStatusT` 。

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>SyncLockWithStatusT：： SyncLockWithStatusT

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
SyncLockWithStatusT(
   _Inout_ SyncLockWithStatusT&& other
);

explicit SyncLockWithStatusT(
   typename SyncTraits::Type sync,
   DWORD status
);
```

### <a name="parameters"></a>參數

*另一方面*<br/>
另一個物件的右值參考 `SyncLockWithStatusT` 。

*保持*<br/>
另一個物件的參考 `SyncLockWithStatusT` 。

*status*<br/>
*另*一個參數或*sync*參數的[status_](#status)資料成員的值。

### <a name="remarks"></a>備註

初始化 `SyncLockWithStatusT` 類別的新執行個體。

第一個函式會 `SyncLockWithStatusT` 從另一個 `SyncLockWithStatusT` 指定的參數， *other*初始化目前的物件，然後使另一個 `SyncLockWithStatusT` 物件失效。 第二個函式是，會將 **`protected`** 目前的 `SyncLockWithStatusT` 物件初始化為不正確狀態。
