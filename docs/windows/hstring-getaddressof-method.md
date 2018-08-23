---
title: 'Hstring:: Getaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e327e2818903396c154be7406ec325695b6b6982
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613361"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf 方法

擷取基礎 HSTRING 控制代碼的指標。

## <a name="syntax"></a>語法

```cpp
HSTRING* GetAddressOf() throw()  
```

## <a name="return-value"></a>傳回值

基礎 HSTRING 控制代碼指標。

## <a name="remarks"></a>備註

此作業之後，就會終結基礎 HSTRING 控制代碼的字串值。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HString 類別](../windows/hstring-class.md)