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
ms.openlocfilehash: ca5056303f77f112e18ef09d606789a5b1c92acd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626308"
---
# <a name="memory-management-examples"></a>記憶體管理：範例

本文說明 MFC 如何針對三種典型的記憶體配置類型，執行框架配置和堆積配置：

- [位元組陣列](#_core_allocation_of_an_array_of_bytes)

- [資料結構](#_core_allocation_of_a_data_structure)

- [物件](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>配置位元組陣列

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>在框架上配置位元組陣列

1. 定義陣列，如下列程式碼所示。 當陣列變數結束其範圍時，會自動刪除陣列並回收其記憶體。

   [!code-cpp[NVC_MFC_Utilities#1](codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>若要在堆積上配置位元組陣列（或任何基本資料類型）

1. 使用**new**運算子搭配此範例中顯示的陣列語法：

   [!code-cpp[NVC_MFC_Utilities#2](codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>若要從堆積解除配置陣列

1. 使用**delete**運算子，如下所示：

   [!code-cpp[NVC_MFC_Utilities#3](codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>資料結構的配置

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>若要在框架上配置資料結構

1. 定義結構變數，如下所示：

   [!code-cpp[NVC_MFC_Utilities#4](codesnippet/cpp/memory-management-examples_4.cpp)]

   結構所佔用的記憶體會在離開其範圍時回收。

#### <a name="to-allocate-data-structures-on-the-heap"></a>若要在堆積上配置資料結構

1. 使用**new**在堆積上配置資料結構，並**刪除**來解除配置它們，如下列範例所示：

   [!code-cpp[NVC_MFC_Utilities#5](codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>物件的配置

#### <a name="to-allocate-an-object-on-the-frame"></a>若要在框架上設定物件

1. 宣告物件，如下所示：

   [!code-cpp[NVC_MFC_Utilities#6](codesnippet/cpp/memory-management-examples_6.cpp)]

   當物件離開其範圍時，會自動叫用物件的析構函式。

#### <a name="to-allocate-an-object-on-the-heap"></a>若要在堆積上設定物件

1. 使用**新**的運算子，它會傳回物件的指標，以便在堆積上設定物件。 使用**delete**運算子將它們刪除。

   下列堆積和框架範例假設此函式 `CPerson` 不接受任何引數。

   [!code-cpp[NVC_MFC_Utilities#7](codesnippet/cpp/memory-management-examples_7.cpp)]

   如果此函式的引數 `CPerson` 是**char**的指標，則框架配置的語句會是：

   [!code-cpp[NVC_MFC_Utilities#8](codesnippet/cpp/memory-management-examples_8.cpp)]

   堆積配置的語句是：

   [!code-cpp[NVC_MFC_Utilities#9](codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>另請參閱

[記憶體管理：堆積配置](memory-management-heap-allocation.md)
