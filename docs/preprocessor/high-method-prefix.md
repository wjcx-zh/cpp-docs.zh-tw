---
title: high_method_prefix
ms.date: 10/18/2018
f1_keywords:
- high_method_prefix
helpviewer_keywords:
- high_method_prefix attribute
ms.assetid: cacebf09-12f5-4919-ad40-939e206e340c
ms.openlocfilehash: 1575b2e3fee461ee0e3987aaf1e770d0611e31ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383748"
---
# <a name="highmethodprefix"></a>high_method_prefix

**C++特定**

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

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)