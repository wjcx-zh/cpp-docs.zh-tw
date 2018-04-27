---
title: is_trivially_copy_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 73928574f2c96da952b7f18908c6b7a175549981
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible 類別

測試類型是否有極簡複製 (trivial copy) 建構函式。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>參數

`T` 要查詢的類型。

## <a name="remarks"></a>備註

如果 `T` 類型是具有 trivial 複製建構函式的類別，則 predicate 類型的執行個體保留 true，否則保留 false。

類別 `T` 的複製建構函式如果符合下列條件，便是極簡複製建構函式：宣告此複製建構函式時是以隱含方式宣告、類別 `T` 沒有任何虛擬函式或虛擬基底、類別 `T` 的所有直接基底都具有極簡複製建構函式、類別類型之所有非靜態資料成員的類別都具有極簡複製建構函式，以及類別之陣列類型的所有非靜態資料成員的類別都具有極簡複製建構函式。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
