---
title: 'Comptrrefbase:: Operator IInspectable * * 運算子 |Microsoft 文件'
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
ms.openlocfilehash: e337f6bbc92718c839fc2bd12c9df9f0caa5d5aa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883455"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator IInspectable** 運算子

支援 WRL 基礎結構，並不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>備註

會轉換目前[ptr_](../windows/comptrrefbase-ptr-data-member.md)資料成員指標--a-指標-將 IInspectable 介面。

如果目前 ComPtrRefBase 不是衍生自 IInspectable，就會發出錯誤。

這項轉換可才 **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** 定義。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ComPtrRefBase 類別](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)