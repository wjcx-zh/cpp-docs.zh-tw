---
title: '&lt;streambuf&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <streambuf>
dev_langs:
- C++
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db05d1b19a67fc54a148d407fd90992a6d37c4c6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213583"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

包含 iostreams 標準標頭 \<streambuf> 來定義範本類別 [basic_streambuf](../standard-library/basic-streambuf-class.md)，這是 iostreams 類別作業的基礎。 此標頭通常會由其他 iostream 標頭所納入；您很少會需要直接將其納入。

## <a name="syntax"></a>語法

```cpp
#include <streambuf>

```

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|特製化`basic_streambuf`使用**char**做為樣板參數。|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|特製化`basic_streambuf`使用**wchar_t**做為樣板參數。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[basic_streambuf 類別](https://msdn.microsoft.com/d9c706ba-ce01-43e0-b0b2-a558fc53ea8d)|此範本類別描述抽象的基底類別，用以衍生資料流緩衝區，其控制項目如何傳入或傳出資料流的特定表示。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
