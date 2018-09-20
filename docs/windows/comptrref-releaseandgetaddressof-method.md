---
title: 'Comptrref:: Releaseandgetaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 004aac42-e135-41ce-8d1d-4c5969d55004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 48c9c748b80bb7900d57e1e0c0aff68d8e1f4ec1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424959"
---
# <a name="comptrrefreleaseandgetaddressof-method"></a>ComPtrRef::ReleaseAndGetAddressOf 方法

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

## <a name="return-value"></a>傳回值

已呈現之介面指標的已刪除**ComPtrRef**物件。

## <a name="remarks"></a>備註

刪除目前**ComPtrRef**物件，並傳回已所代表之介面的指標-到-a-指標**ComPtrRef**物件。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="see-also"></a>另請參閱

[ComPtrRef 類別](../windows/comptrref-class.md)<br/>
[Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)