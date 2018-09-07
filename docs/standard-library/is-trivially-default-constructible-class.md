---
title: is_trivially_default_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73bdd8186f2ce56e4a6ecec0fa4f9468d9da8e8c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102703"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible 類別

測試類型是否有 trivial 預設建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是具有 trivial 建構函式，否則為 false 的類別。

類別預設建構函式*Ty*輕而易舉的事如果：

- 它是以隱含方式宣告的預設建構函式

- 此類別*Ty*沒有虛擬函式

- 此類別*Ty*沒有虛擬基底

- 所有直接基都底類別的*Ty*具有 trivial 建構函式

- 類別類型的所有非靜態資料成員的類別都具有 trivial 建構函式

- 類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 建構函式

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
