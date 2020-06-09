---
title: 記憶體管理：框架配置
ms.date: 11/04/2016
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
ms.openlocfilehash: 1ecf1c08164d1a760fce62457a6019e767ed2605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626306"
---
# <a name="memory-management-frame-allocation"></a>記憶體管理：框架配置

配置框架時會從呼叫函式時設定的「堆疊框架」取用框架名稱。 堆疊框架是一個記憶體區域，會暫時保留函式的引數以及任何為函式區域定義的變數。 框架變數通常稱為「自動」變數，因為編譯器會自動為其配置空間。

框架配置有兩個主要特性。 首先，當您定義區域變數時，包括大型陣列或資料結構，都會在堆疊框架上配置足夠的空間以保留整個變數。 其次，當框架變數超出範圍時，會自動遭到刪除：

[!code-cpp[NVC_MFC_Utilities#10](codesnippet/cpp/memory-management-frame-allocation_1.cpp)]

對於區域函式變數，此範圍轉換會在函式結束時發生，不過，如果使用巢狀大括弧，框架變數的範圍可能會小於函式。 框架變數的這個自動刪除是非常重要的。 在簡單的基本型別（例如**int**或**byte**）、陣列或資料結構的案例中，自動刪除只會回收變數所使用的記憶體。 因為變數已超出範圍，所以是無法存取的。 不過，若是 C++ 物件，自動刪除的程序則較為複雜。

當物件定義為框架變數時，會自動在遇到這個定義的點叫用其建構函式。 當物件超出範圍時，會在回收物件的記憶體之前自動叫用其解構函式。 此自動建構和解構非常方便使用，不過您必須留意自動呼叫，尤其是對解構函式。

在框架上配置物件的主要優點是會自動刪除。 當您在框架上配置物件時，您不必擔心流失的物件會導致記憶體流失  （如需記憶體流失的詳細資訊，請參閱在[MFC 中偵測記憶體](/previous-versions/visualstudio/visual-studio-2010/c99kz476(v=vs.100))流失一文）。框架配置的缺點是框架變數無法在其範圍外使用。 在選擇框架配置或堆積配置時需要考量的另一個因素是，對於大型結構和物件而言，使用堆積通常比儲存體堆疊更為適合，因為堆疊空間通常是有限的。

## <a name="see-also"></a>另請參閱

[記憶體管理](memory-management.md)
