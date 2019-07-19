---
title: '&lt;cstdalign&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdalign>
- cstdalign
- __alignas_is_defined
- __alignof_is_defined
helpviewer_keywords:
- cstdalign header
- __alignas_is_defined
- __alignof_is_defined
ms.assetid: 9d570924-d299-4225-9a58-8c4c820f5903
ms.openlocfilehash: 603a590190c50495aa80f1b41a574149eb8f760a
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342837"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign&gt;

在某些C++標準程式庫執行中, 此標頭包含 C 標準\<程式庫標頭 stdalign >, 並將`std`相關名稱新增至命名空間。 因為該標頭並未在 MSVC 中執行\<, 所以 cstdalign > 標頭`__alignas_is_defined`會`__alignof_is_defined`定義相容性宏和。

> [!NOTE]
> 因為 > stdalign 標頭會定義中C++為關鍵字的宏, 所以不會有任何作用。 \< 在\<中C++, stdalign > 標頭已被取代。 \<Cstdalign > 標頭在 c + + 17 中已被取代, 並已在 draft c + + 20 標準中移除。

## <a name="requirements"></a>需求

**標頭:** \<cstdalign >

**命名空間：** std

## <a name="macros"></a>巨集

| 巨集 | 說明 |
| - | - |
| `__alignas_is_defined` | 擴充至整數常數1的 C 相容性宏。 |
| `__alignof_is_defined` | 擴充至整數常數1的 C 相容性宏。 |

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)\
[C++標準程式庫總覽](cpp-standard-library-overview.md)\
[標準程式庫中C++的執行緒安全](thread-safety-in-the-cpp-standard-library.md)
