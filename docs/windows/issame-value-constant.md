---
title: 'Issame:: Value 常數 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame::value
dev_langs:
- C++
helpviewer_keywords:
- value constant
ms.assetid: ee72deff-54a2-4482-9967-49a86d07f834
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f1f67769f7bab517c6a5010788c3627529f14db2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373514"
---
# <a name="issamevalue-constant"></a>IsSame::value 常數

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

## <a name="remarks"></a>備註

表示一種型別是否與另一個相同。

**值**是 **，則為 true**如果範本參數相同，並**false**範本參數是否不同。

## <a name="requirements"></a>需求

**標頭：** internal.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[IsSame 結構](../windows/issame-structure.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)