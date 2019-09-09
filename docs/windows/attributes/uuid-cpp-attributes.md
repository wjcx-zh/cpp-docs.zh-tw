---
title: uuid (C++ 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: d644f59ac92bf4e39f191c291dd4fef626411c3d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514945"
---
# <a name="uuid-c-attributes"></a>uuid (C++ 屬性)

指定類別或介面的唯一識別碼。

## <a name="syntax"></a>語法

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>參數

*uuid*<br/>
128位的唯一識別碼。

## <a name="remarks"></a>備註

如果介面或類別的定義未指定**uuid** C++屬性，則 Microsoft C++編譯器會提供一個。 當您指定**uuid**時，必須包含引號。

如果您未指定**uuid**，則編譯器會針對在電腦上不同屬性專案中具有相同名稱的介面或類別產生相同的 GUID。

您可以使用 Uuidgen 或 Guidgen 來產生您自己的唯一識別碼。 （若要執行上述任一項工具，請按一下 [**開始**]，然後按一下功能表上的 [**執行**]。 然後輸入所需工具的名稱。）

用於不會同時使用 ATL 的專案時，指定**uuid**屬性與指定[uuid](../../cpp/uuid-cpp.md) **__declspec**修飾詞相同。 若要取得類別的**uuid** ，您可以使用[__uuidof](../../cpp/uuidof-operator.md)

## <a name="example"></a>範例

如需使用**uuid**的範例，請參閱可系結[的範例。](bindable.md)

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**class**、 **struct**、 **interface**、 **union**、 **enum**|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[類別屬性](class-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)