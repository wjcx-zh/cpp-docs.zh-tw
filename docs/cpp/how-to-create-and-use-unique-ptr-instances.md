---
title: 如何：建立和使用 unique_ptr 實例
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 4b3362f71d1ccab0efb03d7e8705c6b3f25f9780
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246529"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>如何：建立和使用 unique_ptr 實例

[Unique_ptr](../standard-library/unique-ptr-class.md)不會共用它的指標。 它無法複製到另一個 `unique_ptr`，以傳值方式傳遞至函式，或用於C++任何需要進行複製的標準程式庫演算法。 只能移動 `unique_ptr`。 這表示記憶體資源的擁有權轉移到另一個 `unique_ptr`，原始 `unique_ptr` 不再擁有它。 因為多重擁有權會增加程序邏輯的複雜度，建議您將物件限制為一個擁有者。 因此，當您需要一般C++物件的智慧型指標時，請使用 `unique_ptr`，而當您建立 `unique_ptr`時，請使用[make_unique](../standard-library/memory-functions.md#make_unique) helper 函數。

下圖說明兩個 `unique_ptr` 執行個體之間的擁有權轉移。

![移動唯一&#95;ptr 的擁有權](media/unique_ptr.png "移動唯一&#95;ptr 的擁有權")

`unique_ptr` 是在C++標準程式庫的 `<memory>` 標頭中定義。 它與原始指標一樣有效率，而且可以在標準程式庫容器C++中使用。 將 `unique_ptr` 實例新增至C++標準程式庫容器的效率很高，因為 `unique_ptr` 的移動函式不需要複製作業。

## <a name="example-1"></a>範例 1

下列範例示範如何建立 `unique_ptr` 執行個體，並在函式之間傳遞這些執行個體。

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

這些範例示範 `unique_ptr` 的這種基本特性：可加以移動，但無法複製。 「移動」會將擁有權轉移到新的 `unique_ptr` 並重設舊的 `unique_ptr`。

## <a name="example-2"></a>範例 2

下列範例示範如何建立 `unique_ptr` 執行個體並在向量中使用這些執行個體。

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

在範圍 for 迴圈中，請注意 `unique_ptr` 是以傳址方式傳遞。 如果您嘗試在這裡以傳值方式傳遞，編譯器就會擲回錯誤，因為 `unique_ptr` 複製建構函式已刪除。

## <a name="example-3"></a>範例 3

下列範例示範如何初始化本身為類別成員的 `unique_ptr`。

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>範例 4

您可以使用[make_unique](../standard-library/memory-functions.md#make_unique)來建立陣列的 `unique_ptr`，但無法使用 `make_unique` 來初始化陣列元素。

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

如需更多範例，請參閱[make_unique](../standard-library/memory-functions.md#make_unique)。

## <a name="see-also"></a>另請參閱

[智慧型指標 (現代 C++)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
