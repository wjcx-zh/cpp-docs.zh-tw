---
title: 'MakeAllocator:: ~ MakeAllocator 解構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- ~MakeAllocator, destructor
ms.assetid: f1299c5f-cc6b-4d4e-85d4-aee1be0e2b0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7115bd3ad6ef1a385b8c2a509f42316c9f8b69bc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607194"
---
# <a name="makeallocatormakeallocator-destructor"></a>MakeAllocator::~MakeAllocator 解構函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
~MakeAllocator();
```

## <a name="remarks"></a>備註

取消初始化目前的執行個體**MakeAllocator**類別。

如有必要，此解構函式也會刪除基礎配置的記憶體。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[MakeAllocator 類別](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)