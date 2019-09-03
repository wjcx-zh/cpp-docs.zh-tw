---
title: once pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 643ad83b672f7b632925383972751a966256eb41
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220534"
---
# <a name="once-pragma"></a>once pragma

指定編譯器在編譯原始程式碼檔案時, 只包含標頭檔一次。

## <a name="syntax"></a>語法

> **#pragma 一次**

## <a name="remarks"></a>備註

使用`#pragma once`可以減少組建時間, 因為編譯器不會在轉譯單位中的第一個`#include`檔案之後再次開啟和讀取檔案。 它稱為*多 include 優化*。 它的效果類似于*include guard*用法, 它會使用預處理器巨集定義來防止多次包含檔案的內容。 它也有助於避免違反*一個定義規則*, 這是因為所有範本、類型、函式和物件在您的程式碼中都不能有一個以上的定義的需求。

例如：

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

對新程式碼我們建議 `#pragma once` 指示詞，因為它不會干擾全域命名空間與前置處理器符號。 它需要較少的輸入、較不分散, 而且不會造成*符號衝突*, 而當不同的標頭檔使用相同的預處理器符號做為 guard 值時, 就會發生錯誤。 這不是C++標準的一部分, 而是由數個通用編譯器所可能。

在相同的檔案中使用 include 防護程式用法和`#pragma once`都沒有任何好處。 編譯器會辨識 include 防護用法, 並以與`#pragma once`指示詞相同的方式來執行多個 include 優化, 如果沒有任何非批註程式碼或預處理器指示詞出現在的標準格式之前或之後:

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

當程式碼必須可移植到未實作為`#pragma once`指示詞的編譯器、維持與現有程式碼的一致性, 或無法進行多重包含優化時, 我們建議使用 include guard。 當檔案系統別名或別名 include 路徑阻止編譯器以標準路徑識別相同的 include 檔案時, 可能會在複雜的專案中發生此問題。

請小心不要使用`#pragma once` , 或使用預處理器符號來控制其效果的標頭檔中的 include guard 用法。 如需這項設計的範例, 請\<參閱 > 標頭檔中的 assert。 也請小心管理您的 include 路徑, 以避免建立包含檔案的多個路徑, 這可能會使包含保護和`#pragma once`的多個 include 優化。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
