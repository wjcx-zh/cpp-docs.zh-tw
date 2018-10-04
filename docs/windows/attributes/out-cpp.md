---
title: out （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.out
dev_langs:
- C++
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c695dbee2b92a2a3fbc5de0830f298b81e63ad8d
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790609"
---
# <a name="out-c"></a>out (C++)

識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。

## <a name="syntax"></a>語法

```cpp
[out]
```

## <a name="remarks"></a>備註

**放大**c + + 屬性具有相同的功能[出](/windows/desktop/Midl/out-idl)MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](bindable.md)範例使用**出**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[參數屬性](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)  