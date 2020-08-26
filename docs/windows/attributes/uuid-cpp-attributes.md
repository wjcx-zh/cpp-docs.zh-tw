---
title: uuid (C++ 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: 9ff8888c26945d7f118e71002e3b3290217b463c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843036"
---
# <a name="uuid-c-attributes"></a>uuid (C++ 屬性)

指定類別或介面的唯一識別碼。

## <a name="syntax"></a>語法

```cpp
[ uuid( "uuid" ) ]
```

### <a name="parameters"></a>參數

*uuid*<br/>
128位的唯一識別碼。

## <a name="remarks"></a>備註

如果介面或類別的定義未指定 `uuid` c + + 屬性，則 Microsoft c + + 編譯器會提供一個屬性。 當您指定時 `uuid` ，必須包含引號。

如果您未指定 `uuid` ，則編譯器會針對相同名稱在電腦上不同屬性專案中的介面或類別產生相同的 GUID。

您可以使用 Uuidgen.exe 或 Guidgen.exe 來產生您自己的唯一識別碼。  (若要執行上述任一項工具，請按一下 [ **開始** ]，然後按一下功能表上的 [ **執行** ]。 然後輸入所需工具的名稱。 ) 

在不使用 ATL 的專案中使用時，指定 `uuid` 屬性與指定 [uuid](../../cpp/uuid-cpp.md) **`__declspec`** 修飾詞相同。 若要取出 `uuid` 類別的，您可以使用 [__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>範例

如需使用的範例，請參閱可系結 [的範例](bindable.md) `uuid` 。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|`class`, `struct`, `interface`, `union`, `enum`|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)
