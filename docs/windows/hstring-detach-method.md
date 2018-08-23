---
title: 'Hstring:: Detach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
dev_langs:
- C++
ms.assetid: 5006ee13-549d-40a8-8dfe-d3fb3b5e18b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b794dea5c8b3b0fcde82c414e0cf24710cafb86
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602493"
---
# <a name="hstringdetach-method"></a>HString::Detach 方法

取消指定的關聯**HString**與其基礎值的物件。

## <a name="syntax"></a>語法

```cpp
HSTRING Detach() throw()  
```

## <a name="return-value"></a>傳回值

基礎**HString**卸離作業啟動之前的值。

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[HString 類別](../windows/hstring-class.md)