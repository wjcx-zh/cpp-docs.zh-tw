---
title: 'Weakreference:: Setunknown 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs:
- C++
helpviewer_keywords:
- SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f127b8435f934e5cf203de2aaa6f2d0c3a58d13
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603066"
---
# <a name="weakreferencesetunknown-method"></a>WeakReference::SetUnknown 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>參數

*unk*  
指標`IUnknown`物件的介面。

## <a name="remarks"></a>備註

設定目前的強式參考**WeakReference**物件與指定的介面指標。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[WeakReference 類別](../windows/weakreference-class1.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)