---
title: once_flag 結構
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: 55c3f90f72857a4e4cd3f9075ce5bae10e14d218
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202723"
---
# <a name="once_flag-structure"></a>once_flag 結構

表示與樣板函式 **`struct`** [call_once](../standard-library/mutex-functions.md#call_once)搭配使用的，以確保初始化程式碼只會呼叫一次，即使有多個執行緒執行也一樣。

## <a name="syntax"></a>語法

結構 once_flag {constexpr once_flag （） noexcept;};

## <a name="remarks"></a>備註

只有預設的函式 `once_flag` **`struct`** 。

可以建立 `once_flag` 類型的物件，但無法複製它們。

## <a name="requirements"></a>需求

**標頭：**\<mutex>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
