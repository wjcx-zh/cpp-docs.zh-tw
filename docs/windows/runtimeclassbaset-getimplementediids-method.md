---
title: 'Runtimeclassbaset:: Getimplementediids 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 907a249090ec58d6379cb58f3d63e15826c1f6ad
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610356"
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>參數

*T*  
型別*實作*參數。

*實作*  
參數所指定的類型指標*T*。

*iidCount*  
若要擷取的介面識別碼的數目上限。

*iid*  
如果這項作業已順利完成，介面型別實作的 Id 陣列*T*。

## <a name="return-value"></a>傳回值

如果成功則為 S_OK否則，會描述錯誤的 HRESULT。

## <a name="remarks"></a>備註

擷取介面 Id 所指定的型別實作的陣列。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[RuntimeClassBaseT 結構](../windows/runtimeclassbaset-structure.md)