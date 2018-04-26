---
title: '&lt;ccomplex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <ccomplex>
dev_langs:
- C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea7ffa0db396242ab072efd01ccdd3def75fea9
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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
