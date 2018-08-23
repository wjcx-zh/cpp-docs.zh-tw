---
title: 'Comptr:: Operator = = 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24ca52eccc814b82e5f9bdd6ddac6458fb5992fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607132"
---
# <a name="comptroperator-operator"></a>ComPtr::operator== 運算子

指出兩個**ComPtr**物件是否相等。

## <a name="syntax"></a>語法

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>參數

*a*  
參考**ComPtr**物件。

*b*  
另一個的參考**ComPtr**物件。

## <a name="return-value"></a>傳回值

第一個運算子會產生 **，則為 true**如果物件是否等於物件*b*否則**false**。

第二個和第三個運算子會產生 **，則為 true**如果物件等於**nullptr**，則為**false**。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)  
[ComPtr 類別](../windows/comptr-class.md)