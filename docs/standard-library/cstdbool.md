---
title: '&lt;cstdbool&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdbool>
- cstdbool
helpviewer_keywords:
- cstdbool header
ms.assetid: 44ccb8b2-d808-4715-8097-58ba09ab33ed
ms.openlocfilehash: ed780e059a5e456731fd6a4f651639e282016f5e
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341097"
---
# <a name="ltcstdboolgt"></a>&lt;cstdbool&gt;

包含 C 標準程式庫標\<頭 stdbool >, 並將相關聯的名稱加入`std`至命名空間。

> [!NOTE]
> 因為 > stdbool 標頭會定義中C++為關鍵字的宏, 所以不會有任何作用。 \< 在\<中C++, stdbool > 標頭已被取代。 \<Cstdbool > 標頭在 c + + 17 中已被取代, 並已在 draft c + + 20 標準中移除。

## <a name="requirements"></a>需求

**標頭:** \<cstdbool >

**命名空間：** std

## <a name="remarks"></a>備註

包含此標頭可確保在 C 標準程式庫標頭中使用外部連結宣告的名稱會`std`在命名空間中宣告。

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)\
[C++標準程式庫總覽](cpp-standard-library-overview.md)\
[標準程式庫中C++的執行緒安全](thread-safety-in-the-cpp-standard-library.md)
