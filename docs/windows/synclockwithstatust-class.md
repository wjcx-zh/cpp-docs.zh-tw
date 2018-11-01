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
ms.openlocfilehash: a3c5c4306dd039a792fe0fd1e57f04d37cc67731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663862"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>參數

*SyncTraits*<br/>
一種類型，可以採取獨佔或共用資源的擁有權。

## <a name="remarks"></a>備註

代表一種類型，可以採取獨佔或共用資源的擁有權。

`SyncLockWithStatusT`類別來實作[Mutex](../windows/mutex-class1.md)並[號誌](../windows/semaphore-class.md)類別。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust:: Synclockwithstatust](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 類別的新執行個體。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[Synclockwithstatust:: Synclockwithstatust](#synclockwithstatust) | 初始化 `SyncLockWithStatusT` 類別的新執行個體。

### <a name="public-methods"></a>公用方法

名稱                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust:: Getstatus](#getstatus) | 擷取目前的等候狀態`SyncLockWithStatusT`物件。
[Synclockwithstatust:: Islocked](#islocked)   | 指出是否目前`SyncLockWithStatusT`物件擁有資源，也就是，則`SyncLockWithStatusT`物件*鎖定*。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                    | 描述
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[Synclockwithstatust:: Status_](#status) | 根據目前的物件上的鎖定作業之後，保留基礎的等候作業的結果`SyncLockWithStatusT`物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers::Details

## <a name="getstatus"></a>Synclockwithstatust:: Getstatus

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>傳回值

以物件為基礎的等候作業的結果`SyncLockWithStatusT`類別，例如[Mutex](../windows/mutex-class1.md)或是[號誌](../windows/semaphore-class.md)。 零 (0) 表示等待作業傳回信號的狀態;否則，另一個狀態發生，例如逾時值過。

### <a name="remarks"></a>備註

擷取目前的等候狀態`SyncLockWithStatusT`物件。

GetStatus() 函式擷取值的基礎[status_](#status)資料成員。 當物件為基礎`SyncLockWithStatusT`類別執行鎖定作業，該物件先等候物件可以使用。 此等待作業的結果會儲存在`status_`資料成員。 可能值`status_`資料成員是等候作業的傳回值。 如需詳細資訊，請參閱的傳回值`WaitForSingleObjectEx()`MSDN Library 中的函式。

## <a name="islocked"></a>Synclockwithstatust:: Islocked

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>備註

指出是否目前`SyncLockWithStatusT`物件擁有資源，也就是，則`SyncLockWithStatusT`物件*鎖定*。

### <a name="return-value"></a>傳回值

**真**如果`SyncLockWithStatusT`物件已鎖定，否則**false**。

## <a name="status"></a>Synclockwithstatust:: Status_

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
DWORD status_;
```

### <a name="remarks"></a>備註

根據目前的物件上的鎖定作業之後，保留基礎的等候作業的結果`SyncLockWithStatusT`物件。

## <a name="synclockwithstatust"></a>Synclockwithstatust:: Synclockwithstatust

支援 WRL 結構，而且不是直接從您的程式碼使用。

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

*other*<br/>
右值參考到另一個`SyncLockWithStatusT`物件。

*sync*<br/>
另一個的參考`SyncLockWithStatusT`物件。

*status*<br/>
值[status_](#status)資料成員*其他*參數或*同步*參數。

### <a name="remarks"></a>備註

初始化 `SyncLockWithStatusT` 類別的新執行個體。

第一個建構函式初始化目前`SyncLockWithStatusT`物件從另一個`SyncLockWithStatusT`參數所指定*其他*，然後則另`SyncLockWithStatusT`物件。 第二個建構函式`protected`，並初始化目前`SyncLockWithStatusT`為無效狀態的物件。
