---
title: const_mem_fun1_t 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::const_mem_fun1_t
dev_langs:
- C++
helpviewer_keywords:
- const_mem_fun1_t class
ms.assetid: 250fac30-9663-4133-9051-6303f76ea259
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 059ad07e50fb6325850d1095940ce084893bf70b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966496"
---
# <a name="constmemfun1t-class"></a>const_mem_fun1_t 類別

配接器類別，這個類別可在使用指標引數初始化 **const** 成員函式 (其接受單一引數) 時，將其當作二元函式物件來呼叫。

## <a name="syntax"></a>語法

```cpp
template <class Result, class Type, class Arg>
class const_mem_fun1_t
 : public binary_function<const Type *, Arg, Result>
{
    explicit const_mem_fun1_t(Result (Type::* _Pm)(Arg) const);
    Result operator()(const Type* _Pleft, Arg right) const;
 };
```

### <a name="parameters"></a>參數

*_Pm*類別的成員函式的指標`Type`轉換成函式物件。

*_Pleft* **const**物件 *_Pm*上呼叫成員函式。

*右*所指定的引數 *_Pm*。

## <a name="return-value"></a>傳回值

具適應性的二元函式。

## <a name="remarks"></a>備註

此範本類別會儲存一份 *_Pm*，它必須是類別的成員函式的指標`Type`，私用成員物件中。 它會定義其成員函式`operator()`做為傳回 ( **_Pleft** -> \* * Pm) (***右邊**) **const**。

## <a name="example"></a>範例

通常並不直接使用 `const_mem_fun1_t` 的建構函式，而協助程式函式 `mem_fun` 可用來調整成員函式。 如需如何使用成員函式配接器的範例，請參閱 [mem_fun](../standard-library/functional-functions.md#mem_fun)。

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
