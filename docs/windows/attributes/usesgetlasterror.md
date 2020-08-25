---
title: 'usesgetlasterror (c + + COM 屬性) '
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: e3d3c292554350d85296971a9bd3620909ef47c7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831628"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

告知呼叫端在呼叫該函式時是否發生錯誤，然後呼叫端可以呼叫 `GetLastError` 以取得錯誤碼。

## <a name="syntax"></a>語法

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>備註

**Usesgetlasterror** c + + 屬性具有與[usesgetlasterror](/windows/win32/Midl/usesgetlasterror) MIDL 屬性相同的功能。

## <a name="example"></a>範例

如需如何使用**usesgetlasterror**的範例，請參閱[idl_module](idl-module.md)範例。

## <a name="requirements"></a>規格需求

| 屬性內容 | 值 |
|-|-|
|**適用於**|**module** 屬性|
|**重複**|否|
|**必要的屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)
