---
title: 項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.entry
dev_langs:
- C++
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a40ad39b089ea68209bfef2997f015c355ca6893
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414039"
---
# <a name="entry"></a>entry

指定匯出的函式或常數 」 模組中，找出 DLL 的進入點。

## <a name="syntax"></a>語法

```cpp
[ entry(
   id
) ]
```

### <a name="parameters"></a>參數

*id*<br/>
進入點的識別碼。

## <a name="remarks"></a>備註

**項目**c + + 屬性具有相同的功能[項目](/windows/desktop/Midl/entry)MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[idl_module](../windows/idl-module.md)範例使用**項目**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|`idl_module` 屬性|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  