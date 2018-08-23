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
ms.openlocfilehash: f9bc6a88ee7dca0bcd4ad2f87fd3aa4c318d8b9d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604761"
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

*id*  
進入點的識別碼。

## <a name="remarks"></a>備註

**項目**c + + 屬性具有相同的功能[項目](http://msdn.microsoft.com/library/windows/desktop/aa366815)MIDL 屬性。

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