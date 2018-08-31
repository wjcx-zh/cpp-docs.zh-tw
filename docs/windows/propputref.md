---
title: propputref |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.propputref
dev_langs:
- C++
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b0b36342b7760eea074fe15506386bb3d7ce6764
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221238"
---
# <a name="propputref"></a>propputref

指定使用參考而非值的屬性設定函式。

## <a name="syntax"></a>語法

```cpp
[propputref]
```

## <a name="remarks"></a>備註

**Propputref** c + + 屬性具有相同的功能[propputref](/windows/desktop/Midl/propputref) MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[可繫結](../windows/bindable.md)範例使用**propputref**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|`propget`, `propput`|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  
[方法屬性](../windows/method-attributes.md)  
[propget](../windows/propget.md)  
[propput](../windows/propput.md)  