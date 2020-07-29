---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 1121bd4e782fca57588d05fb29b5b9b6cdec18e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215604"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

包含 iostreams 標準標頭 \<streambuf> 以定義類別樣板[basic_streambuf](../standard-library/basic-streambuf-class.md)，這對 iostreams 類別的作業是基本的。 此標頭通常會由其他 iostream 標頭所納入；您很少會需要直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|`basic_streambuf`使用 **`char`** 做為範本參數的特製化。|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|`basic_streambuf`使用 **`wchar_t`** 做為範本參數的特製化。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[basic_streambuf 類別](basic-streambuf-class.md)|類別樣板描述用來衍生資料流程緩衝區的抽象基類，其可控制與特定資料流程的表示之間的元素傳輸。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
