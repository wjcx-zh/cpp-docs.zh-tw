---
title: support_error_info （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.support_error_info
dev_langs:
- C++
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c6bb07071efa162b5b33ae5f1dfe72ac7ea02e8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790667"
---
# <a name="supporterrorinfo"></a>support_error_info

實作傳回詳細錯誤的支援。

## <a name="syntax"></a>語法

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>參數

*error_interface*<br/>
介面實作的識別項`IErrorInfo`。

## <a name="remarks"></a>備註

**support_error_info** C++ 屬性支援將目標物件所遇到的詳細內容錯誤傳回給用戶端。 支援錯誤的方法物件`IErrorInfo`，物件必須實作介面。 如需詳細資訊，請參閱 <<c0> [ 支援 IDispatch 和 IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md)。

此屬性會新增[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)類別作為基底類別的目標物件。 這會導致的預設實作`ISupportErrorInfo`，可以在單一介面產生物件錯誤時使用。

## <a name="example"></a>範例

下列程式碼加入預設的支援`ISupportErrorInfo`介面`CMyClass`物件。

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

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**Class - 類別**|
|**可重複**|是|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[COM 屬性](com-attributes.md)<br/>
[類別屬性](class-attributes.md)  