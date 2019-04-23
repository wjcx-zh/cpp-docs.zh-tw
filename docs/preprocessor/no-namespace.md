---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: f6bd60de02bf0166d5cf0b0cd1bc1de56ceda5bf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028713"
---
# <a name="nonamespace"></a>no_namespace
**C++特定**

指定命名空間名稱不是由編譯器產生。

## <a name="syntax"></a>語法

```
no_namespace
```

## <a name="remarks"></a>備註

`#import` 標頭檔中的類型程式庫內容通常是在命名空間中定義。 中指定的命名空間名稱`library`陳述式的原始 IDL 檔案。 如果**no_namespace**指定屬性，則此命名空間不由編譯器產生。

如果您想要使用不同的命名空間的名稱，然後使用[rename_namespace](../preprocessor/rename-namespace.md)改為屬性。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)