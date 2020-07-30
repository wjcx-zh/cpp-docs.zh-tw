---
title: Array 和 WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: 1980fbcd1e2fa8cdaa48e00d2e7de9e45ac96a92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231022"
---
# <a name="array-and-writeonlyarray-ccx"></a>Array 和 WriteOnlyArray (C++/CX)

您可以自由使用一般的 C 樣式陣列或 [`std::array`](../standard-library/array-class-stl.md) c + +/cx 程式（雖然 [`std::vector`](../standard-library/vector-class.md) 通常是較好的選擇），但在任何在中繼資料中發行的 API 中，您必須根據使用方式，將 C 樣式陣列或向量轉換成 [`Platform::Array`](../cppcx/platform-array-class.md) 或 [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) 類型。 [`Platform::Array`](../cppcx/platform-array-class.md)類型的效率和功能都不如 [`std::vector`](../standard-library/vector-class.md) ，因此一般來說，您應該避免在對陣列元素執行許多作業的內部程式碼中使用它。

下列陣列類型可以透過 ABI 傳遞：

1. `const Platform::Array^`

1. `Platform::Array^*`

1. `Platform::WriteOnlyArray`

1. 傳回值`Platform::Array^`

您可以使用這些陣列類型來執行 Windows 執行階段所定義的三種陣列模式。

PassArray
當呼叫端將陣列傳遞給方法時使用。 C + + 輸入參數類型為 **`const`** [`Platform::Array`](../cppcx/platform-array-class.md) \<T> 。

Fillarray」
當呼叫端傳遞陣列供方法填入時使用。 C + + 輸入參數類型為 [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) \<T> 。

ReceiveArray
當呼叫端接收方法所配置的陣列時使用。 在 C++/CX 中，您可以傳回值 Array^ 傳回陣列，也可以傳回做為 Array^ 類型的 out 參數。

## <a name="passarray-pattern"></a>PassArray 模式

當用戶端程式代碼將陣列傳遞給 c + + 方法，而且方法不修改它時，方法會接受陣列做為 `const Array^` 。 在 Windows 執行階段應用程式二進位介面（ABI）層級，這稱為*PassArray*。 下一個範例顯示如何將 JavaScript 中配置的陣列傳遞至讀取此陣列的 C++ 函式。

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

下列程式碼片段示範 C++ 方法：

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>ReceiveArray 模式

在*ReceiveArray*模式中，用戶端程式代碼會宣告陣列，並將它傳遞給方法，以配置它的記憶體並加以初始化。 C + + 輸入參數類型是對 hat 的指標： `Array<T>^*` 。 下列範例顯示如何在 JavaScript 中宣告陣列物件，並將它傳遞至 C++ 函式，此函式會配置記憶體、初始化元素，然後將它傳回至 JavaScript。 JavaScript 將配置的陣列視為傳回值，但 C++ 函式將它視為 out 參數。

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

下列程式碼片段示範實作 C++ 方法的兩種方式：

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>填入陣列

當您想要在呼叫端配置陣列，並在被呼叫端初始化或修改它時，請使用 `WriteOnlyArray`。 下一個範例顯示如何實作使用 `WriteOnlyArray` 的 C++ 函式，以及從 JavaScript 呼叫此函式。

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

下列程式碼片段示範如何實作 C++ 方法：

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>陣列轉換

這個範例示範如何使用 [`Platform::Array`](../cppcx/platform-array-class.md) 來建立其他類型的集合：

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

下一個範例示範如何 [`Platform::Array`](../cppcx/platform-array-class.md) 從 C 樣式陣列中進行構造，並從公用方法中傳回它。

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>不規則陣列

Windows 執行階段類型系統不支援不規則陣列的概念，因此您也就不能使用 `IVector<Platform::Array<T>>` 做為公用方法的傳回值或方法參數。 若要跨 ABI 傳遞不規則陣列或一組序列中的某個序列，請使用 `IVector<IVector<T>^>`。

## <a name="use-arrayreference-to-avoid-copying-data"></a>使用 ArrayReference 可避免複製資料

在某些情況下，資料會透過 ABI 傳遞至 [`Platform::Array`](../cppcx/platform-array-class.md) ，而您最終想要處理 C 樣式陣列中的資料以提高效率，您可以使用[Platform：： ArrayReference](../cppcx/platform-arrayreference-class.md)來避免額外的複製作業。 當您將當做 [`Platform::ArrayReference`](../cppcx/platform-arrayreference-class.md) 引數傳遞給採用的參數時 `Platform::Array` ， `ArrayReference` 會將資料直接儲存到您指定的 C 樣式陣列中。 請注意， `ArrayReference` 不會鎖定來源資料，因此如果在呼叫完成之前修改或刪除另一個執行緒上的資料，結果會是未定義的。

下列程式碼片段示範如何將作業的結果複製 [`DataReader`](/uwp/api/windows.storage.streams.datareader) 到中 `Platform::Array` （一般模式），以及如何替代，將 `ArrayReference` 資料直接複製到 C 樣式陣列中：

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>避免將陣列公開為屬性

一般而言，您應該避免將 `Platform::Array` 類型公開為 ref 類別中的屬性，因為即使用戶端程式碼只嘗試存取單一元素，也會傳回整個陣列。 當您需要將序列容器公開為公用 ref 類別中的屬性時， [`Windows::Foundation::IVector`](/uwp/api/windows.foundation.collections.ivector-1) 是較佳的選擇。 在私用或內部 Api 中（不會發行至中繼資料），請考慮使用標準 c + + 容器，例如 [`std::vector`](../standard-library/vector-class.md) 。

## <a name="see-also"></a>另請參閱

[型別系統](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空間參考](../cppcx/namespaces-reference-c-cx.md)
