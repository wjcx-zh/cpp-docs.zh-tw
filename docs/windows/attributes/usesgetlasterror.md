---
title: usesgetlasterror (C++ COM 屬性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: 9f050bbf69edf1ab8327a283299cb5e687ce5380
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032202"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

會告知呼叫端，是否沒有發生錯誤時呼叫該函式，然後呼叫端可以再呼叫`GetLastError`擷取錯誤碼。

## <a name="syntax"></a>語法

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>備註

**Usesgetlasterror** C++屬性具有相同的功能[usesgetlasterror](/windows/desktop/Midl/usesgetlasterror) MIDL 屬性。

## <a name="example"></a>範例

請參閱[idl_module](idl-module.md)如需範例示範如何使用**usesgetlasterror**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**模組**屬性|
|**可重複**|否|
|**必要屬性**|None|
|**無效屬性**|None|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)