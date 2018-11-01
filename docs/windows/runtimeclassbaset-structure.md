---
title: RuntimeClassBaseT 結構
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 3dd55c322e7da3be3f888c4faa88172fd0c17672
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456845"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 結構

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>參數

*RuntimeClassTypeT*<br/>
指定一或多個旗標欄位[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)列舉值。

## <a name="remarks"></a>備註

提供 helper 方法來`QueryInterface`作業和取得的介面識別碼。

## <a name="members"></a>成員

### <a name="protected-methods"></a>保護方法

名稱                                                         | 描述
------------------------------------------------------------ | -----------------------------------------------------------------------------
[Runtimeclassbaset:: Asiid](#asiid)                           | 擷取指定的介面 ID 的指標
[Runtimeclassbaset:: Getimplementediids](#getimplementediids) | 擷取介面 Id 所指定的型別實作的陣列。

## <a name="inheritance-hierarchy"></a>繼承階層

`RuntimeClassBaseT`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="asiid"></a>Runtimeclassbaset:: Asiid

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>參數

*T*<br/>
實作介面識別碼參數所指定的型別*riid*。

*implements*<br/>
範本參數所指定類型的變數*T*。

*riid*<br/>
要擷取的介面識別碼。

*ppvObject*<br/>
如果這項作業成功時，參數所指定的指標-至-a-介面的指標*riid*。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，會描述錯誤的 HRESULT。

### <a name="remarks"></a>備註

擷取指定的介面 ID 的指標

## <a name="getimplementediids"></a>Runtimeclassbaset:: Getimplementediids

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>參數

*T*<br/>
型別*實作*參數。

*implements*<br/>
參數所指定的類型指標*T*。

*iidCount*<br/>
若要擷取的介面識別碼的數目上限。

*iid*<br/>
如果這項作業已順利完成，介面型別實作的 Id 陣列*T*。

### <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，會描述錯誤的 HRESULT。

### <a name="remarks"></a>備註

擷取介面 Id 所指定的型別實作的陣列。
