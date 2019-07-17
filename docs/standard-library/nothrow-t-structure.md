---
title: nothrow_t 結構
ms.date: 11/04/2016
f1_keywords:
- nothrow_t
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
ms.openlocfilehash: bd65b5006326850522a251cbcf7d655133a1aa8a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245571"
---
# <a name="nothrowt-structure"></a>nothrow_t 結構

此類別可用來作為 new 運算子的函式參數，以指出函式應該要傳回 Null 指標來回報配置失敗，而非擲回例外狀況。

## <a name="syntax"></a>語法

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>備註

此結構可協助編譯器選取正確的建構函式版本。 [nothrow](../standard-library/new-functions.md#nothrow) 與 `std::nothrow_t` 類型的物件同義。

## <a name="example"></a>範例

如需如何使用 `std::nothrow_t` 作為函式參數的範例，請參閱 [operator new](../standard-library/new-operators.md#op_new) 和 [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)。
