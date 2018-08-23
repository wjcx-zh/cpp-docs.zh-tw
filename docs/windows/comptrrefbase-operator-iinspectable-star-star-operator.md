---
title: 'Comptrrefbase:: Operator IInspectable * * 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f711a9d1f5fe92e5f35bf333fc0b3473fc0eebf4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604402"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>Comptrrefbase:: Operator IInspectable\* \*運算子

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>備註

將目前的轉換[ptr_](../windows/comptrrefbase-ptr-data-member.md)資料成員指標至-a-指標-對`IInspectable`介面。

會發出錯誤，如果目前**ComPtrRefBase**不是衍生自`IInspectable`。

這項轉換可才`__WRL_CLASSIC_COM__`定義。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ComPtrRefBase 類別](../windows/comptrrefbase-class.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)