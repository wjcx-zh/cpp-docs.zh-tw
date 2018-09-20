---
title: 'Comptr:: Operator ！ = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator!=
dev_langs:
- C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce6e3357582abe94fdc538932e49e773c37f116b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384687"
---
# <a name="comptroperator-operator"></a>ComPtr::operator!= 運算子

指出兩個**ComPtr**物件是否不相等。

## <a name="syntax"></a>語法

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>參數

*a*<br/>
參考**ComPtr**物件。

*b*<br/>
另一個的參考**ComPtr**物件。

## <a name="return-value"></a>傳回值

第一個運算子會產生 **，則為 true**如果物件是否不等於物件*b*否則**false**。

第二個和第三個運算子會產生 **，則為 true**如果物件是否不等於**nullptr**，則為**false**。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)<br/>
[ComPtr 類別](../windows/comptr-class.md)