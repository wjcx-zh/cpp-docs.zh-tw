---
title: once
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 6061fe77960aa64e2dcb39db05897ef0e7fb5f2e
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039872"
---
# <a name="once"></a>once
指定編譯原始程式碼檔案時，編譯器只能包含 (開啟) 檔案一次。

## <a name="syntax"></a>語法

```
#pragma once
```

## <a name="remarks"></a>備註

善用`#pragma once`可以縮短建置時間，因為編譯器不會開啟和讀取檔案，在第一個之後`#include`的轉譯單位中的檔案。 這指*多個 include 最佳化*。 它有的效果類似於`#include guard`慣用語，使用前置處理器巨集定義來防止多次包含檔案的內容。 這也有助於避免違反*一個定義規則*—，所有的範本、 類型、 函數和物件有不超過一個定義程式碼中的需求。

例如: 

```
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

對新程式碼我們建議 `#pragma once` 指示詞，因為它不會干擾全域命名空間與前置處理器符號。 它需要的輸入較少，較不令人分心，而且不會造成符號衝突，不同標頭檔使用相同的前置處理器符號做為防護值時造成的錯誤。 它不是 C++ Standard 的一部分，但它可能由數個常見編譯器實作。

在同一個檔案中同時使用 #include 防護慣用語和 `#pragma once` 並沒有任何益處。 如果在此慣用語的標準形式之前或之後沒有非註解程式碼或前置處理器指示詞，編譯器會辨識 #include 防護慣用語並以與 `#pragma once` 指示詞的相同方式實作多個 include 最佳化：

```
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

我們建議`#include guard`慣用語，當程式碼必須是以編譯器不會實作可攜式`#pragma once`指示詞，以維護一致性與現有的程式碼，或當多個 include 最佳化不可能。 在檔案系統別名 include 路徑防止編譯器依正式路徑識別相同 include 檔案的複雜專案中，便可能發生此情況。

請小心不要使用`#pragma once`或`#include guard`慣用語都是設計成包含許多次，來控制其效果使用前置處理器符號的標頭檔中。 如需這項設計的範例，請參閱\<assert.h> > 標頭檔。 也請小心管理 include 路徑，以避免建立多重路徑包含的檔案，可以打敗多個 include 最佳化，同時`#include guard`s 和`#pragma once`。

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)