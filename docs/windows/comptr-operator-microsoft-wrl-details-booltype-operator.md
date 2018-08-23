---
title: 'Comptr:: booltype 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 135c6d851be5de8f2eb976baf015f2ef449600c0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595969"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType 運算子

指出是否**ComPtr**管理介面的物件存留期。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

## <a name="return-value"></a>傳回值

如果介面是與此相關聯**ComPtr**的地址[boolstruct:: Member](../windows/boolstruct-member-data-member.md)資料成員，否則**nullptr**。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ComPtr 類別](../windows/comptr-class.md)  
[ComPtr::Get 方法](../windows/comptr-get-method.md)