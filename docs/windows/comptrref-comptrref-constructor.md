---
title: 'Comptrref:: Comptrref 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef, constructor
ms.assetid: ce2d2533-fef6-4b2d-b088-6f3db01df5a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 606f9560f6d490e1d50d94dd12103713781c4f1b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603756"
---
# <a name="comptrrefcomptrref-constructor"></a>ComPtrRef::ComPtrRef 建構函式

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>參數

*ptr*  
基礎值的另一個**ComPtrRef**物件。

## <a name="remarks"></a>備註

初始化的新執行個體**ComPtrRef**到另一個類別的指定指標**ComPtrRef**物件。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ComPtrRef 類別](../windows/comptrref-class.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)