---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: ae79ce9245bb1c0425c3e9b92dd27b52fa443dba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179603"
---
# <a name="tlbid"></a>tlbid

**C++特定**

允許載入主要類型程式庫以外的程式庫。

## <a name="syntax"></a>語法

```
tlbid(number)
```

### <a name="parameters"></a>參數

*number*<br/>
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

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)