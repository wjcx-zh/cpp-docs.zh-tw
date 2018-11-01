---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 31b71f7c195a7e2ee649b40197551e4ff5efda2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584506"
---
# <a name="tlbid"></a>tlbid

**C + + 特定**

允許載入主要類型程式庫以外的程式庫。

## <a name="syntax"></a>語法

```
tlbid(number)
```

### <a name="parameters"></a>參數

*數字*<br/>
`filename` 中類型程式庫的號碼。

## <a name="remarks"></a>備註

如果多個型別程式庫會建置成單一 DLL，您可以使用載入主要類型程式庫以外的程式庫**tlbid**。

例如: 

```cpp
#import <MyResource.dll> tlbid(2)
```

等於：

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**END c + + 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)