---
title: out （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.out
dev_langs:
- C++
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1b90222faedf298f75bfea72c661a3f23f26eaed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394868"
---
# <a name="out-c"></a>out (C++)

識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。

## <a name="syntax"></a>語法

```cpp
[out]
```

## <a name="remarks"></a>備註

**放大**c + + 屬性具有相同的功能[出](/windows/desktop/Midl/out-idl)MIDL 屬性。

## <a name="example"></a>範例

請參閱 [bindable](../windows/bindable.md) 範例中 **out**的範例使用。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|介面參數|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|無|

如需有關屬性內容的詳細資訊，請參閱 [屬性內容](../windows/attribute-contexts.md)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](../windows/idl-attributes.md)<br/>
[參數屬性](../windows/parameter-attributes.md)<br/>
[defaultvalue](../windows/defaultvalue.md)<br/>
[id](../windows/id.md)  