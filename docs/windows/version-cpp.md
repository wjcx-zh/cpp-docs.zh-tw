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
ms.openlocfilehash: 60a5ad42f83d9e9528fd5bdc4c8d3e62254a3677
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438729"
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

*version*<br/>
版本號碼`coclass`。 如果未指定，1.0 會置於.idl 檔案。

## <a name="remarks"></a>備註

**版本**c + + 屬性具有相同的功能[版本](/windows/desktop/Midl/version)MIDL 屬性且會傳遞至產生的.idl 檔案。

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

[編譯器屬性](../windows/compiler-attributes.md)<br/>
[類別屬性](../windows/class-attributes.md)  