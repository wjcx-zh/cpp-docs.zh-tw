---
title: tlbid 匯入屬性
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 364fb224b0f2769cb0933e71d18ff70768189328
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216529"
---
# <a name="tlbid-import-attribute"></a>tlbid 匯入屬性

**C++特殊**

允許載入主要類型程式庫以外的程式庫。

## <a name="syntax"></a>語法

> **#import***類型-程式庫-dll***tlbid (** *數位* **)**

### <a name="parameters"></a>參數

*項數*\
型別程式庫 *-dll*中型別程式庫的數目。

## <a name="remarks"></a>備註

如果將多個類型程式庫內建于單一 DLL 中, 則可以使用**tlbid**載入主要型別程式庫以外的程式庫。

例如：

```cpp
#import <MyResource.dll> tlbid(2)
```

等於：

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
