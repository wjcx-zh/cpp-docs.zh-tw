---
title: hash 結構 (C++ 標準程式庫)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- thread/std::hash
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
ms.openlocfilehash: bb230d401d5061f4951f8007f93c3a28ce3dab03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405010"
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
