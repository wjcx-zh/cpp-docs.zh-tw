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
ms.openlocfilehash: 39052024224b1a78a84b2d9503957b8fff09b96f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208287"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

會告知呼叫端，是否沒有發生錯誤時呼叫該函式，然後呼叫端可以再呼叫`GetLastError`擷取錯誤碼。

## <a name="syntax"></a>語法

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>備註

**Usesgetlasterror** c + + 屬性具有相同的功能[usesgetlasterror](/windows/desktop/Midl/usesgetlasterror) MIDL 屬性。

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