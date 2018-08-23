---
title: pointer_default |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 391b30251235fdd15ec1e96304e956740cb58f1f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610144"
---
# <a name="pointerdefault"></a>pointer_default

指定出現在參數清單的最上層指標除外的所有指標的預設指標屬性。

## <a name="syntax"></a>語法

```cpp
[ pointer_default(
   value
) ]
```

### <a name="parameters"></a>參數

*值*  
描述此指標類型的值： **ptr**， **ref**，或**唯一**。

## <a name="remarks"></a>備註

**Pointer_default** c + + 屬性具有相同的功能[pointer_default](http://msdn.microsoft.com/library/windows/desktop/aa367141) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[defaultvalue](../windows/defaultvalue.md)範例使用**pointer_default**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**interface**|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[介面屬性](../windows/interface-attributes.md)  