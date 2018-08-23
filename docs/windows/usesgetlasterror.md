---
title: usesgetlasterror |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.usesgetlasterror
dev_langs:
- C++
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7921ff48adf2f987844557f9af3be5adcd6736de
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602758"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

會告知呼叫端，是否沒有發生錯誤時呼叫該函式，然後呼叫端可以再呼叫`GetLastError`擷取錯誤碼。

## <a name="syntax"></a>語法

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>備註

**Usesgetlasterror** c + + 屬性具有相同的功能[usesgetlasterror](http://msdn.microsoft.com/library/windows/desktop/aa367297) MIDL 屬性。

## <a name="example"></a>範例

請參閱[idl_module](../windows/idl-module.md)如需範例示範如何使用**usesgetlasterror**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**模組**屬性|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)  