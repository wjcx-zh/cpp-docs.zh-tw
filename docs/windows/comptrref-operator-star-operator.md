---
title: 'Comptrref:: Operator * 運算子 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator*
dev_langs:
- C++
helpviewer_keywords:
- operator* operator
ms.assetid: 0287ca7a-4ce1-47f7-bab6-714fca3e04bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5bb6bc06f65f53f919197b5350db8aacc268013f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602955"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator* 運算子

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
InterfaceType* operator *();
```

## <a name="return-value"></a>傳回值

目前所代表之介面指標**ComPtrRef**物件。

## <a name="remarks"></a>備註

擷取目前所代表之介面指標**ComPtrRef**物件。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ComPtrRef 類別](../windows/comptrref-class.md)  
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)