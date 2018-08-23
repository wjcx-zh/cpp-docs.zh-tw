---
title: 'Verifyinheritancehelper:: Verify 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cfcbb57694fc18944d199c1d4c74d8c74a335783
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599111"
---
# <a name="verifyinheritancehelperverify-method"></a>VerifyInheritanceHelper::Verify 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
static void Verify();
```

## <a name="remarks"></a>備註

測試目前的範本參數所指定的兩個介面，並決定是否要將一個介面衍生自其他。

如果有一個介面不衍生自其他，就會發出錯誤。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[VerifyInheritanceHelper 結構](../windows/verifyinheritancehelper-structure.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)