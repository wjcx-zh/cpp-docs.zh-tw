---
title: size_is (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: a7b990a708bafba78c9dc4153315f8b7b20351ba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033225"
---
# <a name="sizeis"></a>size_is

指定記憶體的大小配置大小的指標、 調整大小來調整大小的指標，以及單一或多維陣列的指標。

## <a name="syntax"></a>語法

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>參數

*expression*<br/>
所配置的記憶體大小調整大小的指標。

## <a name="remarks"></a>備註

**Size_is** C++屬性具有相同的功能[size_is](/windows/desktop/Midl/size-is) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[first_is](first-is.md)如需如何指定的陣列區段的範例。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|欄位**結構**或是**聯集**，參數的介面，介面方法|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|`max_is`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)