---
title: 項目 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 95eb37898d4934740e1520df758ed33d3dd4c79a
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790658"
---
# <a name="entry"></a>entry

指定匯出的函式或常數 」 模組中，找出 DLL 的進入點。

## <a name="syntax"></a>語法

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>參數

*id*<br/>
進入點的識別碼。

## <a name="remarks"></a>備註

**項目**c + + 屬性具有相同的功能[項目](/windows/desktop/Midl/entry)MIDL 屬性。

## <a name="example"></a>範例

範例，請參閱[idl_module](idl-module.md)範例使用**項目**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|`idl_module` 屬性|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)  