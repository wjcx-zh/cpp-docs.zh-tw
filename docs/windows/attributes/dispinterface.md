---
title: 分配介面 （c + + COM 屬性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dispinterface
helpviewer_keywords:
- dispinterface attribute
ms.assetid: 61c5a4a1-ae92-47e9-8ee4-f847be90172b
ms.openlocfilehash: 6fd5010dc20d03c518206d81919e3beafbcaa9a9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038456"
---
# <a name="dispinterface"></a>dispinterface

將介面放入 .idl 檔案中作為分派介面。

## <a name="syntax"></a>語法

```cpp
[dispinterface]
```

## <a name="remarks"></a>備註

**dispinterface** C++ 屬性在介面前面時，會將介面放在所產生 .idl 檔案的程式庫區塊內。

除非您指定基底類別，否則分派介面將衍生自 `IDispatch`。 您必須指定分派介面成員的 [id](id.md) 。

MIDL 文件中 [dispinterface](/windows/desktop/Midl/dispinterface) 的用法範例：

```cpp
dispinterface helloPro
   { interface hello; };
```

不適用於 **dispinterface** 屬性。

## <a name="example"></a>範例

如需如何使用 [dispinterface](bindable.md) 的範例，請參閱 **bindable**範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|`dual`, `object`, `oleautomation`, `local`, `ms_union`|

如需詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[依使用方式分類的屬性](attributes-by-usage.md)<br/>
[uuid](uuid-cpp-attributes.md)<br/>
[dual](dual.md)<br/>
[自訂](custom-cpp.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)