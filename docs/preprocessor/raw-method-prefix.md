---
title: raw_method_prefix
ms.date: 03/27/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: c3015cf8b51646d25fd8f36a7336c63dc8fe492b
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565593"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**C + + 特定**

指定不同的前置詞，避免發生名稱衝突。

## <a name="syntax"></a>語法

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>參數

*前置詞*<br/>
要使用的前置詞。

## <a name="remarks"></a>備註

低層級的屬性和方法，由成員函式的前置詞**raw_** 以避免與高階錯誤處理成員函式的名稱衝突。

> [!NOTE]
> 效果**raw_method_prefix**屬性將不會變更的存在[raw_interfaces_only](raw-interfaces-only.md)屬性。 **Raw_method_prefix**一定會優先於`raw_interfaces_only`中指定前置詞。 如果這兩個屬性會在相同`#import`陳述式，然後藉由指定的前置詞**raw_method_prefix**屬性使用。

**END c + + 特定的**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)