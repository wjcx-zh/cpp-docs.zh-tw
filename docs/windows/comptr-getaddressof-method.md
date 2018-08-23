---
title: 'Comptr:: Getaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 972a41d0-c2ef-4ae3-b2cd-77cc45156ac9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 98609ce9cc15940586d626c52d24b5ca506164e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598990"
---
# <a name="comptrgetaddressof-method"></a>ComPtr::GetAddressOf 方法

擷取位址[ptr_](../windows/comptr-ptr-data-member.md)資料成員，其中包含這所代表之介面的指標**ComPtr**。

## <a name="syntax"></a>語法

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

## <a name="return-value"></a>傳回值

變數的位址。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ComPtr 類別](../windows/comptr-class.md)