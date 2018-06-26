---
title: 記憶體管理： 範例 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21efd095a1d8e89c140ef39072a753c300a3043b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929303"
---
# <a name="memory-management-examples"></a>記憶體管理：範例
本文說明 MFC 如何執行框架配置和堆積配置每個記憶體配置一般的三種：  
  
-   [位元組陣列](#_core_allocation_of_an_array_of_bytes)  
  
-   [一種資料結構](#_core_allocation_of_a_data_structure)  
  
-   [物件](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a> 配置的位元組陣列  
  
#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>配置框架上的位元組陣列  
  
1.  定義陣列，如下列程式碼所示。 陣列，會自動刪除，並對其進行記憶體回收的陣列變數離開範圍時。  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]  
  
#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>若要在堆積上配置一個陣列的位元組 （或任何基本資料類型）  
  
1.  使用**新**運算子陣列語法範例所示：  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]  
  
#### <a name="to-deallocate-the-arrays-from-the-heap"></a>若要解除配置堆積中的陣列  
  
1.  使用**刪除**運算子，如下所示：  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a> 一種資料結構的配置  
  
#### <a name="to-allocate-a-data-structure-on-the-frame"></a>配置框架上的資料結構  
  
1.  定義結構變數，如下所示：  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]  
  
     當超出範圍時，會開始回收結構所佔用的記憶體。  
  
#### <a name="to-allocate-data-structures-on-the-heap"></a>配置在堆積上的資料結構  
  
1.  使用**新**配置在堆積上的資料結構和**刪除**取消配置，如下列範例所示：  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a> 物件的配置  
  
#### <a name="to-allocate-an-object-on-the-frame"></a>配置框架上的物件  
  
1.  物件的宣告，如下所示：  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]  
  
     當物件離開範圍時，會自動叫用物件的解構函式。  
  
#### <a name="to-allocate-an-object-on-the-heap"></a>配置在堆積上物件  
  
1.  使用**新**運算子，就會傳回物件的指標，配置在堆積上的物件。 使用**刪除**運算子將它們刪除。  
  
     下列的堆積和框架範例假設`CPerson`建構函式接受任何引數。  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]  
  
     如果引數`CPerson`建構函式是指向**char**，是框架配置的陳述式：  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]  
  
     堆積配置的陳述式是：  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [記憶體管理：堆積配置](../mfc/memory-management-heap-allocation.md)

