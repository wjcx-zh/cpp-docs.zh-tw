---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: ca5f53d67bb32e59c20d1d440879144f0a617c66
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686015"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

包含 iostreams 標準標頭 \<streambuf > 以定義類別樣板[basic_streambuf](../standard-library/basic-streambuf-class.md)，這是 iostreams 類別作業的基本作業。 此標頭通常會由其他 iostream 標頭所納入；您很少會需要直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedef

|類型名稱|描述|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|使用**char**做為範本參數之 `basic_streambuf` 的特製化。|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|使用**wchar_t**做為範本參數之 `basic_streambuf` 的特製化。|

### <a name="classes"></a>類別

|執行個體|描述|
|-|-|
|[basic_streambuf 類別](basic-streambuf-class.md)|類別樣板描述用來衍生資料流程緩衝區的抽象基類，其可控制與特定資料流程的表示之間的元素傳輸。|

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostream 慣例](../standard-library/iostreams-conventions.md)
