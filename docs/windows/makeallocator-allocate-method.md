---
title: 'Makeallocator:: Allocate 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4dd68a3c678b7877db63167fd2c0d48a1daa7ad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411829"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
__forceinline void* Allocate();
```

## <a name="return-value"></a>傳回值

如果成功，已配置的記憶體; 指標否則，請**nullptr**。

## <a name="remarks"></a>備註

配置記憶體，並將它與目前相關聯**MakeAllocator**物件。

配置的記憶體大小是目前所指定之類型的大小**MakeAllocator**樣板參數。

開發人員必須覆寫只**Allocate()** 方法，以實作不同的記憶體配置模型。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[MakeAllocator 類別](../windows/makeallocator-class.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)