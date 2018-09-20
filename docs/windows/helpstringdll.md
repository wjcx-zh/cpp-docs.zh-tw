---
title: helpstringdll |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstringdll
dev_langs:
- C++
helpviewer_keywords:
- helpstringdll attribute [C++]
ms.assetid: 121271fa-f061-492b-b87f-bbfcf4b02e7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1eecedca8988c95466a3f257fbc77768b7c67b3b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392862"
---
# <a name="helpstringdll"></a>helpstringdll

指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。

## <a name="syntax"></a>語法

```cpp
[ helpstringdll(
   "string"
) ]
```

### <a name="parameters"></a>參數

*string*<br/>
用來執行文件字串查閱 DLL。

## <a name="remarks"></a>備註

**Helpstringdll** c + + 屬性具有相同的功能[helpstringdll](/windows/desktop/Midl/helpstringdll) MIDL 屬性。

## <a name="example"></a>範例

```cpp
// cpp_attr_ref_helpstringdll.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib", helpstringdll="xx.dll")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMyI
{
   HRESULT xxx();
};
```

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**，**介面**，介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)<br/>
[介面屬性](../windows/interface-attributes.md)<br/>
[類別屬性](../windows/class-attributes.md)<br/>
[方法屬性](../windows/method-attributes.md)  