---
title: hash 結構 (C++ 標準程式庫)| Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- thread/std::hash
dev_langs:
- C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6f00b3c3136a4a2df96667d0f99f195339c60f1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056616"
---
# <a name="hash-structure-c-standard-library"></a>hash 結構 (C++ 標準程式庫)

定義傳回由 `Val` 唯一決定值的成員函式。 成員函式會定義 [hash](../standard-library/hash-class.md) 函式，適用於將 `thread::id` 類型的值對應到索引值的分佈。

## <a name="syntax"></a>語法

```cpp
template <>
struct hash<thread::id> :
    public unary_function<thread::id, size_t>
{
    size_t operator()(thread::id Val) const;

};
```

## <a name="requirements"></a>需求

**標頭：** \<執行緒 >

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<thread>](../standard-library/thread.md)<br/>
[unary_function 結構](../standard-library/unary-function-struct.md)<br/>
