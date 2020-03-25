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
ms.openlocfilehash: d1109e769352d412df8348822e05b66063159ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214223"
---
# <a name="activateinstance-function"></a>ActivateInstance 函式

註冊並抓取指定的類別識別碼中所定義之指定類型的實例。

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
要啟動的類型。

*activatableClassId*<br/>
定義參數*T*之類別識別碼的名稱。

*執行個體*<br/>
當此作業完成時，為*T*之實例的參考。

## <a name="return-value"></a>傳回值

如果成功，則 S_OK;否則，就會出現錯誤 HRESULT，指出錯誤的原因。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Windows：： Foundation

## <a name="see-also"></a>另請參閱

[Windows::Foundation 命名空間](windows-foundation-namespace.md)
