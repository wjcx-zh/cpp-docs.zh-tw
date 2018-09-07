---
title: is_trivially_copy_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1924b82f7c3035ea2aecb463199558c9ead45c91
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102061"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible 類別

測試類型是否有極簡複製 (trivial copy) 建構函式。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是具有 trivial 複製建構函式，否則為 false 的類別。

類別的複製建構函式*T*只是如果它以隱含方式宣告，此類別的一般*T*沒有虛擬函式或虛擬基底類別的所有直接基底*T*有trivial 複製建構函式，類別類型的所有非靜態資料成員的類別具有 trivial 複製建構函式和類別的類型陣列的所有非靜態資料成員的類別具有 trivial 複製建構函式。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
