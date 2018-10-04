---
title: 本機 （c + + COM 屬性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e24efe4d4ad4f4e28b93503ecf82936e3113c1ed
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791007"
---
# <a name="local-c"></a>local (C++)

介面的標頭中使用時，可讓您使用 MIDL 編譯器為標頭的產生器。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。

## <a name="syntax"></a>語法

```cpp
[local]
```

## <a name="remarks"></a>備註

**本機**c + + 屬性具有相同的功能[本機](/windows/desktop/Midl/local)MIDL 屬性。

## <a name="example"></a>範例

請參閱[call_as](call-as.md)如需如何使用的範例**本機**。

## <a name="requirements"></a>需求

### <a name="attribute-context"></a>屬性內容

|||
|-|-|
|**適用於**|**介面**，介面方法|
|**可重複**|否|
|**必要屬性**|無|
|**無效屬性**|`dispinterface`|

如需詳細資訊，請參閱 <<c0> [ 屬性內容](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另請參閱

[IDL 屬性](idl-attributes.md)<br/>
[介面屬性](interface-attributes.md)<br/>
[方法屬性](method-attributes.md)<br/>
[call_as](call-as.md)  