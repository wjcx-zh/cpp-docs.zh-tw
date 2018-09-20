---
title: 'Implementshelper:: Fillarraywithiid 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
dev_langs:
- C++
helpviewer_keywords:
- FillArrayWithIid method
ms.assetid: f60035ee-b7d6-4a08-966d-f88c646944c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d570eaf3872f5d281d769e77298f9186d35e5a26
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410425"
---
# <a name="implementshelperfillarraywithiid-method"></a>ImplementsHelper::FillArrayWithIid 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>參數

*index*<br/>
以零為起始的索引，指出起始的陣列項目，這項作業。 這項作業完成時， *index*都會遞增 1。

*iid*<br/>
Iid 類型的陣列。

## <a name="remarks"></a>備註

插入至指定的陣列項目目前的第零個範本參數所指定的介面識別碼。

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ImplementsHelper 結構](../windows/implementshelper-structure.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)