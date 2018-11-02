---
title: 如何：建立和使用 unique_ptr 執行個體
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: 13823b34042d8658d0d690e6657e1f41db50f788
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610245"
---
# <a name="how-to-create-and-use-uniqueptr-instances"></a>如何：建立和使用 unique_ptr 執行個體

A [unique_ptr](../standard-library/unique-ptr-class.md)不共用其指標。 無法將它複製到另一個`unique_ptr`、 傳值方式傳遞至函式，或用於任何需要製作複本的 c + + 標準程式庫演算法。 只能移動 `unique_ptr`。 這表示記憶體資源的擁有權轉移到另一個 `unique_ptr`，原始 `unique_ptr` 不再擁有它。 因為多重擁有權會增加程序邏輯的複雜度，建議您將物件限制為一個擁有者。 因此，當您需要一般 c + + 物件的智慧型指標，使用`unique_ptr`，以及當您建構`unique_ptr`，使用[make_unique](../standard-library/memory-functions.md#make_unique) helper 函式。

下圖說明兩個 `unique_ptr` 執行個體之間的擁有權轉移。

![移動的唯一擁有權&#95;ptr](../cpp/media/unique_ptr.png "unique_ptr")

`unique_ptr` 定義於`<memory>`c + + 標準程式庫中的標頭。 它完全與原始指標一樣有效率，並可以用於 c + + 標準程式庫容器。 新增`unique_ptr`執行個體，以 c + + 標準程式庫容器是有效率因為的移動建構函式`unique_ptr`就不需要複製作業。

## <a name="example"></a>範例

下列範例示範如何建立 `unique_ptr` 執行個體，並在函式之間傳遞這些執行個體。

[!code-cpp[stl_smart_pointers#210](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

這些範例示範 `unique_ptr` 的這種基本特性：可加以移動，但無法複製。 「移動」會將擁有權轉移到新的 `unique_ptr` 並重設舊的 `unique_ptr`。

## <a name="example"></a>範例

下列範例示範如何建立 `unique_ptr` 執行個體並在向量中使用這些執行個體。

[!code-cpp[stl_smart_pointers#211](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

在範圍 for 迴圈中，請注意 `unique_ptr` 是以傳址方式傳遞。 如果您嘗試在這裡以傳值方式傳遞，編譯器就會擲回錯誤，因為 `unique_ptr` 複製建構函式已刪除。

## <a name="example"></a>範例

下列範例示範如何初始化本身為類別成員的 `unique_ptr`。

[!code-cpp[stl_smart_pointers#212](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example"></a>範例

您可以使用[make_unique](../standard-library/memory-functions.md#make_unique)來建立`unique_ptr`陣列，但是您無法使用`make_unique`初始化陣列元素。

[!code-cpp[stl_smart_pointers#213](../cpp/codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

如需其他範例，請參閱 < [make_unique](../standard-library/memory-functions.md#make_unique)。

## <a name="see-also"></a>另請參閱

[智慧型指標](../cpp/smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)