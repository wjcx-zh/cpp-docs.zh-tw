---
title: 作法：建立及使用 shared_ptr 執行個體
ms.custom: how-to
ms.date: 05/22/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: d0ee1a5e8c5d26e8e0bec060ffe3d5fea30ce0fa
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866141"
---
# <a name="how-to-create-and-use-shared_ptr-instances"></a>HOW TO：建立及使用 shared_ptr 執行個體

`shared_ptr` 類型是 C++ 標準程式庫中的一種智慧型指標，是為有一個以上的擁有者可能必須管理物件在記憶體中的存留期之情節而設計。 在您初始化 `shared_ptr` 之後，您可以函式引數中的值予以複製、傳送以及指派至其他 `shared_ptr` 執行個體。 所有執行個體都會指向相同的物件，並共用對一個每當新的 `shared_ptr` 加入、超出範圍或重設時會遞增和遞減參考計數的「控制區塊」的存取。 當參考計數達到零時，控制區塊會刪除記憶體資源和自己本身。

下圖顯示幾個指向一個記憶體位置的 `shared_ptr` 執行個體。

![共用指標圖表](../cpp/media/shared_ptr.png "共用指標圖表")

## <a name="example-setup"></a>範例設定

以下範例假設您已包含必要的標頭，並宣告了必要類型，如此處所示：

```cpp
// shared_ptr-examples.cpp
// The following examples assume these declarations:
#include <algorithm>
#include <iostream>
#include <memory>
#include <string>
#include <vector>

struct MediaAsset
{
    virtual ~MediaAsset() = default; // make it polymorphic
};

struct Song : public MediaAsset
{
    std::wstring artist;
    std::wstring title;
    Song(const std::wstring& artist_, const std::wstring& title_) :
        artist{ artist_ }, title{ title_ } {}
};

struct Photo : public MediaAsset
{
    std::wstring date;
    std::wstring location;
    std::wstring subject;
    Photo(
        const std::wstring& date_,
        const std::wstring& location_,
        const std::wstring& subject_) :
        date{ date_ }, location{ location_ }, subject{ subject_ } {}
};

using namespace std;

int main()
{
    // The examples go here, in order:
    // Example 1
    // Example 2
    // Example 3
    // Example 4
    // Example 6
}
```

## <a name="example-1"></a>範例 1

在任何可能的情況下，請在初次建立記憶體資源時使用 [make_shared](../standard-library/memory-functions.md#make_shared) 函式來建立 `shared_ptr`。 `make_shared` 是無例外狀況之虞。 它會使用相同的呼叫來配置控制區塊的記憶體及資源，減少建構的額外負荷。 若您不使用 `make_shared`，便必須使用明確的 `new` 運算式來建立物件，才能將物件傳遞至 `shared_ptr` 建構函式。 下列範例顯示各種宣告和初始化 `shared_ptr` 及新物件的方式。

[!code-cpp[stl_smart_pointers#1](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>範例 2

下列範例顯示如何宣告和初始化 `shared_ptr` 執行個體，其具有已被另一個 `shared_ptr` 配置之物件的共用擁有權。 假設 `sp2` 是已初始化的 `shared_ptr`。

[!code-cpp[stl_smart_pointers#2](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>範例 3

當您在 C++ 標準程式庫容器內使用會複製元素的演算法時，`shared_ptr` 也相當實用。 您可以包裝 `shared_ptr` 中的項目，然後將它複製到能夠辨識只有需要時才有效 (不再需要時則無效) 之基礎記憶體的其他容器中。 下列範例顯示如何在向量中的 `remove_copy_if` 執行個體上運用 `shared_ptr` 演算法。

[!code-cpp[stl_smart_pointers#4](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>範例 4

您可以使用 `dynamic_pointer_cast`、`static_pointer_cast` 和 `const_pointer_cast` 轉換 `shared_ptr`。 這些函式類似 `dynamic_cast`、`static_cast` 和 `const_cast` 運算子。 下列範例顯示如何測試在基底類別的 `shared_ptr` 向量中每個項目的衍生類型，然後複製項目並顯示其相關資訊。

[!code-cpp[stl_smart_pointers#5](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>範例 5

您可以透過下列方式將 `shared_ptr` 傳遞至另一個函式：

- 以傳值方式傳遞 `shared_ptr`。 這會叫用複製建構函式、遞增參考計數以及讓被呼叫端成為擁有者。 此作業中有少量的額外負荷，也可能視您傳遞的 `shared_ptr` 物件多寡而變多。 請在呼叫者和被呼叫者之間的隱含或明確程式碼合約要求被呼叫者成為擁有者時，使用此選項。

- 以傳址或 const 的傳址方式傳遞 `shared_ptr`。 在這種情況下，參考計數不會遞增，並且只要呼叫者沒有離開範圍，被呼叫者都能存取該指標。 或者，被呼叫者可以決定根據參考建立一個 `shared_ptr`，並成為共用擁有者。 當呼叫端不了解被呼叫端或者您必須傳遞 `shared_ptr` 且要基於效能考量避免複製作業時，請使用這個選項。

- 將基底指標或參考傳遞至基礎物件。 這可讓被呼叫者使用物件，但不會讓它共用擁有權或延長存留期。 若被呼叫者從原始指標建立 `shared_ptr`，則新的 `shared_ptr` 會獨立於原始的 shared_ptr，並且不會控制基礎資源。 當呼叫端和被呼叫端之間的協定明確指定呼叫端保留 `shared_ptr` 存留期的擁有權時，請使用這個選項。

- 在您決定如何傳遞 `shared_ptr` 時，請判斷被呼叫者是否必須共用基礎資源的擁有權。 「擁有者」是一個只要需要時就讓基礎資源存活的物件或函式。 如果呼叫端必須確保被呼叫端可以延長指標的壽命為超過其 (函式的) 存留期，請使用第一個選項。 如果您不在乎被呼叫端是否延長存留期，則以傳址方式傳遞，並讓被呼叫端決定是否複製。

- 若您必須讓 helper 函式存取基礎指標，並且您知道 helper 函式只會在呼叫函式傳回之前使用指標並傳回，則該函式便不需要共用基礎指標的擁有權。 它只需要存取呼叫端之 `shared_ptr` 的存留期內的指標。 在這種情況下，以傳址方式傳遞 `shared_ptr`，或傳遞基礎物件的原始指標或參考是安全的。 以這種方式傳遞有一小小的效能優點，並且也可以協助您表達程式設計的意圖。

- 在某些情況下，例如在 `std::vector<shared_ptr<T>>` 中，您可能必須將每個 `shared_ptr` 傳遞到 Lambda 運算式主體或具名函式物件。 若 lambda 或函式並未儲存指標，請以傳址方式傳遞 `shared_ptr` 來避免叫用每個元素的複製建構函式。

## <a name="example-6"></a>範例 6

以下範例顯示 `shared_ptr` 如何多載各種比較運算子，以啟用 `shared_ptr` 執行個體所擁有之記憶體的指標比較。

[!code-cpp[stl_smart_pointers#3](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>另請參閱

[智慧型指標 (現代 C++)](../cpp/smart-pointers-modern-cpp.md)
