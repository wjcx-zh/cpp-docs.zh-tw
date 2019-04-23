---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 26527ca69c66c73f5d41084dc42df5faa34481d3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030537"
---
# <a name="noimplementation"></a>no_implementation
**C++特定**

不產生 .tli 標頭，其中包含包裝函式成員函式的實作。

## <a name="syntax"></a>語法

```
no_implementation
```

## <a name="remarks"></a>備註

如果已指定這個屬性，則會產生 .tlh 標頭 (具有公開類型程式庫項目的宣告)，但沒有 `#include` 陳述式可包含 .tli 標頭檔。

這個屬性用於搭配[implementation_only](../preprocessor/implementation-only.md)。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)