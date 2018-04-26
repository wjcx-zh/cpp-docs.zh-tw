---
title: char_traits&lt;char&gt; 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c74e00d9a1f8678539c4f722d48c409d1505b39
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="chartraitsltchargt-struct"></a>char_traits&lt;char&gt; 結構

結構，其為類型 `char` 之元素的樣板結構 **char_traits\<CharType>** 的特製化。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用操作此 `char` 類型物件的程式庫函式。

## <a name="example"></a>範例

請參閱樣板類別 [char_traits 類別](../standard-library/char-traits-struct.md)的 typedef 和成員函式
