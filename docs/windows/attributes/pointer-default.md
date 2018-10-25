---
title: pointer_default （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 994a4a48c5199c3efb05a00331656b3b23a2a0c0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067038"
---
# <a name="pointerdefault"></a>pointer_default

指定出現在參數清單的最上層指標除外的所有指標的預設指標屬性。

## <a name="syntax"></a>語法

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>參數

*值*<br/>
描述此指標類型的值： **ptr**， **ref**，或**唯一**。

## <a name="remarks"></a>備註

**Pointer_default** c + + 屬性具有相同的功能[pointer_default](/windows/desktop/Midl/pointer-default) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[defaultvalue](defaultvalue.md)範例使用**pointer_default**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)