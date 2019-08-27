---
title: '&lt;ccomplex&gt;'
ms.date: 07/11/2019
f1_keywords:
- <ccomplex>
- ccomplex
helpviewer_keywords:
- ccomplex header
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: 5b5383b1eca4fda72f5f9e3a78637373acbcf7ab
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341136"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

包含C++標準程式庫標頭[ \<複雜 >](complex.md)。

> [!NOTE]
> C 標準程式庫\<> 標頭不\<包含在 x > 中, 因為它實際上是以複雜 > 和C++ \<h > \<中的多載來取代。 這會讓\<x > 標頭重複。 在\<中C++, 複雜的 .h > 標頭已被取代。 \<X > 標頭在 c + + 17 中已被取代, 並已在 draft c + + 20 標準中移除。

## <a name="requirements"></a>需求

**標頭:** \<x >

**命名空間：** std

## <a name="remarks"></a>備註

因為可能`clog`與`clog` [iostream >中\<](iostream.md)所\<宣告的發生衝突, 所以不會在`std`命名空間中定義在複雜 .h > 中宣告的名稱。

## <a name="see-also"></a>另請參閱

[\<複雜 >](complex.md)\
[\<cmath>](cmath.md)\
[標頭檔參考](cpp-standard-library-header-files.md)\
[C++標準程式庫總覽](cpp-standard-library-overview.md)\
[標準程式庫中C++的執行緒安全](thread-safety-in-the-cpp-standard-library.md)
