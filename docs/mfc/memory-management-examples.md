---
title: 記憶體管理：範例
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
ms.openlocfilehash: 3a1e647175b7b5294e672efbf234e3ae2853e411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367840"
---
# <a name="memory-management-examples"></a>記憶體管理：範例

本文介紹 MFC 如何對三種典型的記憶體分配執行幀分配和堆分配:

- [位元陣列](#_core_allocation_of_an_array_of_bytes)

- [資料結構](#_core_allocation_of_a_data_structure)

- [物件](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>位元陣列的配置

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>在幀上配置位元陣列

1. 定義陣列,如以下代碼所示。 當陣列變數退出其範圍時,陣列將自動刪除,其記憶體將回收。

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>在堆上配置位元組(或任何基元資料類型)

1. 將**新**運算子與此範例中所示的陣列語法一起使用:

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>從堆中取消分配陣列

1. 使用**刪除**運算子,如下所示:

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>資料結構的配置

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>在幀上配置資料結構

1. 定義結構變數,如下所示:

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   當結構退出其作用域時,將回收結構佔用的記憶體。

#### <a name="to-allocate-data-structures-on-the-heap"></a>在堆上配置資料結構

1. 使用**new**在堆上配置資料結構**並刪除**以取消分配它們,如以下範例所示:

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>物件的配置

#### <a name="to-allocate-an-object-on-the-frame"></a>在幀上分配物件

1. 宣告物件如下:

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   當物件退出其範圍時,將自動調用物件的析構函數。

#### <a name="to-allocate-an-object-on-the-heap"></a>在堆上配置物件

1. 使用返回指向物件的指標**的新**運算符在堆上分配物件。 使用**刪除**運算子刪除它們。

   以下堆和幀示例假定`CPerson`構造函數不採用任何參數。

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   如果建構函數的`CPerson`參數是指向**char**的指標,則幀分配的語句為:

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   堆分配的敘述是:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>另請參閱

[記憶體管理：堆積配置](../mfc/memory-management-heap-allocation.md)
