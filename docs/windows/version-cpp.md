---
title: 版本 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a46a2f9b18a45e7ea627488881b0289e733ddd7b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608963"
---
# <a name="version-c"></a>version (C++)

識別類別的多個版本之間的特定版本。

## <a name="syntax"></a>語法

```cpp
[ version(
   "version"
) ]
```

### <a name="parameters"></a>參數

*version*  
版本號碼`coclass`。 如果未指定，1.0 會置於.idl 檔案。

## <a name="remarks"></a>備註

**版本**c + + 屬性具有相同的功能[版本](http://msdn.microsoft.com/library/windows/desktop/aa367306)MIDL 屬性且會傳遞至產生的.idl 檔案。

## <a name="example"></a>範例

請參閱[可繫結](../windows/bindable.md)的範例使用的範例**版本**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**類別**，**結構**|
|**可重複**|否|
|**必要屬性**|**coclass**|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[編譯器屬性](../windows/compiler-attributes.md)  
[類別屬性](../windows/class-attributes.md)  