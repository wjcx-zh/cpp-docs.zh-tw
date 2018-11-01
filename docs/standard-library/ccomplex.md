---
title: '&lt;ccomplex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ccomplex>
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
ms.openlocfilehash: e0f8c31afac0608b4de66bd10602264666d39426
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667931"
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;

包括 C++ 標準程式庫標頭 [\<complex>](../standard-library/complex.md)，它會有效率地包括標準 C 程式庫標頭 \<complex.h>，並將相關聯的名稱新增至 `std` 命名空間。

## <a name="syntax"></a>語法

```cpp
#include <ccomplex>

```

## <a name="remarks"></a>備註

包含此標頭可保證，透過使用 Standard C 程式庫標頭中的外部連結所宣告的名稱會在 `std` 命名空間中宣告。

名稱 `clog` (宣告於 \<complex.h> 中) 未定義在 `std` 命名空間中，因為可能發生與 `clog` (宣告於 [\<iostream>](../standard-library/iostream.md) 中) 的衝突。

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫概觀](../standard-library/cpp-standard-library-overview.md)<br/>
