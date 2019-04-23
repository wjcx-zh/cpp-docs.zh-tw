---
title: ActivateInstance 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 43aa34153f0e71dd665090243ff2288bff704404
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029076"
---
# <a name="activateinstance-function"></a>ActivateInstance 函式

註冊，並擷取在指定的類別識別碼所定義之指定類型的執行個體

## <a name="syntax"></a>語法

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>參數

*T*<br/>
若要啟用一種類型。

*activatableClassId*<br/>
參數定義的類別識別碼的名稱*T*。

*instance*<br/>
這項作業完成時，執行個體的參考*T*。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，發生錯誤的 HRESULT，表示錯誤的原因。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Windows::Foundation

## <a name="see-also"></a>另請參閱

[Windows::Foundation 命名空間](windows-foundation-namespace.md)