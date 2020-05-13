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
ms.openlocfilehash: 77bcb8336e4650de7ed01a067fa1bdd7ec0ba3e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374271"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <typename SyncTraits>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>參數

*同步特徵*<br/>
可以獲取資源的獨佔或共用擁有權的類型。

## <a name="remarks"></a>備註

表示可以獲取資源的獨佔或共用擁有權的類型。

該`SyncLockWithStatusT`類用於實現[Mutex](mutex-class.md)和[訊號量](semaphore-class.md)類。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[與狀態同步鎖定::與狀態同步鎖定](#synclockwithstatust) | 將 `SyncLockWithStatusT` 類別的新執行個體初始化。

### <a name="protected-constructors"></a>受保護的建構函式

名稱                                                             | 描述
---------------------------------------------------------------- | --------------------------------------------------------------
[與狀態同步鎖定::與狀態同步鎖定](#synclockwithstatust) | 將 `SyncLockWithStatusT` 類別的新執行個體初始化。

### <a name="public-methods"></a>公用方法

名稱                                         | 描述
-------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------
[與狀態同步鎖定::取得狀態](#getstatus) | 檢索當前`SyncLockWithStatusT`物件的等待狀態。
[與狀態同步鎖定::已鎖定](#islocked)   | 指示當前物件是否`SyncLockWithStatusT`擁有資源;如果當前物件是否擁有資源,則表明當前物件是否擁有資源。也就是說,`SyncLockWithStatusT`物件已*鎖定*。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                                    | 描述
--------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------
[與狀態同步鎖定::status_](#status) | 保存基於當前`SyncLockWithStatusT`對象的鎖定操作后基礎等待操作的結果。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝::D

## <a name="synclockwithstatustgetstatus"></a><a name="getstatus"></a>與狀態同步鎖定::取得狀態

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
DWORD GetStatus() const;
```

### <a name="return-value"></a>傳回值

基於`SyncLockWithStatusT`類的物件(如[Mutex](mutex-class.md)或[Semaphore)](semaphore-class.md)的等待操作的結果。 零 (0) 表示等待操作返回了信號狀態;否則,則發生另一種狀態,例如已經過的超時值。

### <a name="remarks"></a>備註

檢索當前`SyncLockWithStatusT`物件的等待狀態。

GetStatus() 函數檢索基礎[status_](#status)資料成員的值。 當基於`SyncLockWithStatusT`類的物件執行鎖定操作時,該物件首先等待該物件變為可用。 等待操作的結果儲存在資料成員中`status_`。 `status_`數據成員的可能值是等待操作的返回值。 有關詳細資訊,請參閱 MSDN`WaitForSingleObjectEx()`庫中 函數的返回值。

## <a name="synclockwithstatustislocked"></a><a name="islocked"></a>與狀態同步鎖定::已鎖定

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
bool IsLocked() const;
```

### <a name="remarks"></a>備註

指示當前物件是否`SyncLockWithStatusT`擁有資源;如果當前物件是否擁有資源,則表明當前物件是否擁有資源。也就是說,`SyncLockWithStatusT`物件已*鎖定*。

### <a name="return-value"></a>傳回值

如果物件已`SyncLockWithStatusT`鎖定,**則為 true;** 否則,**假**。

## <a name="synclockwithstatuststatus_"></a><a name="status"></a>與狀態同步鎖定::status_

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
DWORD status_;
```

### <a name="remarks"></a>備註

保存基於當前`SyncLockWithStatusT`對象的鎖定操作后基礎等待操作的結果。

## <a name="synclockwithstatustsynclockwithstatust"></a><a name="synclockwithstatust"></a>與狀態同步鎖定::與狀態同步鎖定

支援 WRL 基礎結構,不打算直接從代碼中使用。

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

*其他*<br/>
對另一個`SyncLockWithStatusT`物件的 rvalue 引用。

*sync*<br/>
對另一個`SyncLockWithStatusT`物件的引用。

*狀態*<br/>
*另*一個參數或*同步*參數的數據成員[status_](#status)的值。

### <a name="remarks"></a>備註

將 `SyncLockWithStatusT` 類別的新執行個體初始化。

第一個建構函數從參數*其他*`SyncLockWithStatusT`指定的`SyncLockWithStatusT`另一個 初始化當前物件,然後`SyncLockWithStatusT`使另一個 物件無效。 第二個構造函數`protected`是 ,`SyncLockWithStatusT`並將當前 物件初始化為無效狀態。
