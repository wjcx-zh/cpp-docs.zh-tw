---
title: 'Comptr:: Releaseandgetaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f4aee13808fd55c42319aab90c13af7922ed9d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394828"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf 方法

釋放與這個相關聯的介面**ComPtr** ，然後擷取的地址[ptr_](../windows/comptr-ptr-data-member.md)資料成員，其中包含已釋放之介面的指標。

## <a name="syntax"></a>語法

```cpp
T** ReleaseAndGetAddressOf();
```

## <a name="return-value"></a>傳回值

地址[ptr_](../windows/comptr-ptr-data-member.md)資料成員**ComPtr**。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[ComPtr 類別](../windows/comptr-class.md)<br/>
[ComPtr::ptr_ 資料成員](../windows/comptr-ptr-data-member.md)