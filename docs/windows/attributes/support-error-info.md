---
title: 'support_error_info (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: cf02af793b97c55de4c52280ad2795a460a98d9f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832174"
---
# <a name="support_error_info"></a>support_error_info

實作傳回詳細錯誤的支援。

## <a name="syntax"></a>語法

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>參數

*error_interface*<br/>
執行之介面的識別碼 `IErrorInfo` 。

## <a name="remarks"></a>備註

**support_error_info** C++ 屬性支援將目標物件所遇到的詳細內容錯誤傳回給用戶端。 為了讓物件支援錯誤，介面的方法 `IErrorInfo` 必須由物件來執行。 如需詳細資訊，請參閱 [支援 IDispatch 和 IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md)。

此屬性會將 [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) 類別當成基底類別新增至目標物件。 這會導致的預設執行 `ISupportErrorInfo` ，而且可以在單一介面產生物件錯誤時使用。

## <a name="example"></a>範例

下列程式碼會將介面的預設支援新增 `ISupportErrorInfo` 至 `CMyClass` 物件。

```cpp
// cpp_attr_ref_support_error_info.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="mymod")];
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]
__interface IMyErrors
{
};

[ coclass, support_error_info("IMyErrors"),
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]
class CMyClass
{
};
```

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**`class`**|
|**重複**|是|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)
