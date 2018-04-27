---
title: input_iterator_tag 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- xutility/std::input_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c2a6384075151c38c3ec57d024e409edccda8bd
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag 結構

一種類別，可為代表輸入迭代器的 **iterator_category** 函式提供傳回類型。

## <a name="syntax"></a>語法

input_iterator_tag 結構{};

## <a name="remarks"></a>備註

分類標籤類別會用來當作可供選取演算法的編譯標籤。 範本函式必須尋找其迭代器引數的最明確分類，如此它才能在編譯階段使用最有效率的演算法。 針對每個 `Iterator` 類型的迭代器，必須將 `iterator_traits`< `Iterator`> **::iterator_category** 定義為描述迭代器行為的最明確分類標籤。

當 **Iter** 描述可當作輸入迭代器的物件時，此類型與 **iterator**\< **Iter**> **::iterator_category** 相同。

## <a name="example"></a>範例

如需如何使用 **iterator_tag** 的範例，請參閱 [iterator_traits](../standard-library/iterator-traits-struct.md) 或 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)。

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
