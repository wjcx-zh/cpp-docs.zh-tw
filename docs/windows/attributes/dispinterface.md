---
title: 分配介面 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dispinterface
dev_langs:
- C++
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b02244e0576f99cc0a6940f2ee4a13511cfbe6f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790321"
---
# <a name="dispinterface"></a>dispinterface

將介面放入 .idl 檔案中作為分派介面。

## <a name="syntax"></a>語法

```cpp
[dispinterface]
```

## <a name="remarks"></a>備註

**dispinterface** C++ 屬性在介面前面時，會將介面放在所產生 .idl 檔案的程式庫區塊內。

除非您指定基底類別，否則分派介面將衍生自 `IDispatch`。 您必須指定[識別碼](id.md)分派介面成員。

用法範例[dispinterface](/windows/desktop/Midl/dispinterface) MIDL 文件中：

```cpp
dispinterface helloPro
   { interface hello; };
```

不適用於 **dispinterface** 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)如需如何使用的範例**dispinterface**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

如需詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[依使用方式分類的屬性](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[custom](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)  