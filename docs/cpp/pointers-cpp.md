---
title: 指標（C++）
ms.date: 11/19/2019
description: 關於 Microsoft C++中的原始指標和智慧型指標。
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 21dcc55048e9e378f370f25254e1910b05e49d69
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246413"
---
# <a name="pointers-c"></a>指標（C++）

指標是一個變數，可儲存物件的記憶體位址。 指標廣泛用於 C 和C++三個主要用途：

- 若要在堆積上配置新物件，
- 將函數傳遞至其他函式
- 反覆運算陣列或其他資料結構中的元素。

在 C 樣式程式設計中，會在所有這些案例中使用*原始指標*。 不過，原始指標是許多嚴重的程式設計錯誤的來源。 因此，強烈建議您不要使用它們，除非它們提供顯著的效能優點，而且不明確地說明哪一個指標是負責刪除物件的*擁有指標*。 新式C++提供*智慧指標*，用於設定物件、用於遍歷資料結構的*反覆運算*器，以及用於傳遞函式的*lambda 運算式*。 藉由使用這些語言和程式庫設施，而不是原始指標，您可以讓程式更安全、更容易進行調試，以及更輕鬆地瞭解和維護。 如需詳細資訊，請參閱[智慧型指標](smart-pointers-modern-cpp.md)、[反覆運算](../standard-library/iterators.md)器和[Lambda 運算式](lambda-expressions-in-cpp.md)。

## <a name="in-this-section"></a>本節內容

- [原始指標](raw-pointers.md)
- [Const 和 volatile 指標](const-and-volatile-pointers.md)
- [new 和 delete 運算子](new-and-delete-operators.md)
- [智慧型指標](smart-pointers-modern-cpp.md)
- [如何：建立和使用 unique_ptr 實例](how-to-create-and-use-unique-ptr-instances.md)
- [如何：建立和使用 shared_ptr 實例](how-to-create-and-use-shared-ptr-instances.md)
- [如何：建立和使用 weak_ptr 實例](how-to-create-and-use-weak-ptr-instances.md)
- [如何：建立及使用 CComPtr 和 CComQIPtr 實例](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>另請參閱

[迭代器](../standard-library/iterators.md)</br>
[Lambda 運算式](lambda-expressions-in-cpp.md)
