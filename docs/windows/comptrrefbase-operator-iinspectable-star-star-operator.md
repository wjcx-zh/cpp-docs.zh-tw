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
ms.openlocfilehash: 0c23ba7ba476b44b44f48b76119776e2f2cb188e
ms.sourcegitcommit: 04d327940787df1297b72d534f388a035d472af0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2018
ms.locfileid: "39181142"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>Comptrrefbase:: Operator IInspectable\* \*運算子

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>備註

將目前的轉換[ptr_](../windows/comptrrefbase-ptr-data-member.md)資料成員指標至-a-指標-對 IInspectable 介面。

如果目前的 ComPtrRefBase 不是衍生自 IInspectable，就會發出錯誤。

這項轉換可才 **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** 定義。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ComPtrRefBase 類別](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)
