---
title: 隱藏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.hidden
dev_langs:
- C++
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 350f1c7c844bd386191b2a236f5bc4ada4e1672a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204524"
---
# <a name="hidden"></a>隱藏

表示項目存在，但不是會顯示在使用者導向的瀏覽器中。

## <a name="syntax"></a>語法

```cpp
[hidden]
```

## <a name="remarks"></a>備註

**隱藏**c + + 屬性具有相同的功能[隱藏](/windows/desktop/Midl/hidden)MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](../windows/bindable.md)如需如何使用的範例**隱藏**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**，**類別**，**結構**、 方法、 屬性|
|**可重複**|否|
|**必要屬性**|**coclass** (當套用至**類別**或是**結構**)|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[介面屬性](../windows/interface-attributes.md)  
[類別屬性](../windows/class-attributes.md)  
[方法屬性](../windows/method-attributes.md)  