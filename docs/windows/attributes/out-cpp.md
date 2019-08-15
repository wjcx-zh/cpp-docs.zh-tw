---
title: out (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 11c8e4473f0b849fab7846a825b90da3ed9f036f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514281"
---
# <a name="out-c"></a>out (C++)

識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。

## <a name="syntax"></a>語法

```cpp
[out]
```

## <a name="remarks"></a>備註

**out** C++ 屬性的功能與 [out](/windows/win32/Midl/out-idl) MIDL 屬性相同。

## <a name="example"></a>範例

請參閱 [bindable](bindable.md) 範例中 **out**的範例使用。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)