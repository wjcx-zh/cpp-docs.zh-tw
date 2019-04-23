---
title: raw_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 23250b524fdaa2181c8e28229ccec680ffdae715
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033251"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes

**C++特定**

為三個屬性方法指定替代的前置詞。

## <a name="syntax"></a>語法

```
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>參數

*GetPrefix*<br/>
若要使用的前置詞`propget`方法。

*PutPrefix*<br/>
若要使用的前置詞`propput`方法。

*PutRefPrefix*<br/>
若要使用的前置詞`propputref`方法。

## <a name="remarks"></a>備註

根據預設，低階`propget`， `propput`，並`propputref`方法會公開由成員函式的名稱前置詞**get_**， **put_**，和**putref_** 分別。 這些前置詞與標頭檔中使用由 MIDL 所產生的名稱相容。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)