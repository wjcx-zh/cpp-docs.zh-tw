---
title: helpstring |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae2d5121e17a9325ec45143e7e90e7d2a211f380
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223094"
---
# <a name="helpstring"></a>helpstring

指定用來描述所套用之項目的字元字串。

## <a name="syntax"></a>語法

```cpp
[ helpstring(
   "string"
) ]
```

### <a name="parameters"></a>參數

*string*  
[說明] 字串文字。

## <a name="remarks"></a>備註

**Helpstring** c + + 屬性具有相同的功能[helpstring](/windows/desktop/Midl/helpstring) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[defaultvalue](../windows/defaultvalue.md)如需如何使用的範例**helpstring**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**， **typedef**，**類別**、 方法、 屬性|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[介面屬性](../windows/interface-attributes.md)  
[類別屬性](../windows/class-attributes.md)  
[方法屬性](../windows/method-attributes.md)  
[Typedef、Enum、Union 和 Struct 屬性](../windows/typedef-enum-union-and-struct-attributes.md)  
[helpfile](../windows/helpfile.md)  
[helpcontext](../windows/helpcontext.md)  