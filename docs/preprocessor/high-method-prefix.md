---
title: high_method_prefix |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- high_method_prefix attribute
ms.assetid: cacebf09-12f5-4919-ad40-939e206e340c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fb69b9fbb7ede0ca458007aec1bee2cf38e286f
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807714"
---
# <a name="highmethodprefix"></a>high_method_prefix

**C + + 特定**

指定用來命名高階屬性和方法的前置詞。

## <a name="syntax"></a>語法

```
high_method_prefix("Prefix")
```

### <a name="parameters"></a>參數

*前置詞*<br/>
要使用的前置詞。

## <a name="remarks"></a>備註

根據預設，高階錯誤處理屬性和方法會由名稱不含前置詞的成員函式公開。 其名稱來自於類型程式庫。

**END c + + 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)