---
title: 指標 (C++)
ms.date: 11/19/2019
description: 關於微軟C++的原始指標和智慧指標。
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 485cee667fa288bff76fdeac7c9f229355c276d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371909"
---
# <a name="pointers-c"></a>指標 (C++)

指標是存儲物件的記憶體位址的變數。 指標在 C 和C++中廣泛使用,主要有三個目的:

- 在堆上分配新物件,
- 將函數傳遞給其他函式
- 反覆運算陣列或其他數據結構中的元素。

在 C 樣式的編程中,*原始指標*用於所有這些方案。 但是,原始指標是許多嚴重程式設計錯誤的根源。 因此,強烈建議不使用它們,除非它們提供了顯著的性能優勢,並且對於哪個指標是負責刪除對象的*擁有指標*沒有歧義。 現代C++提供用於分配物件的*智慧指標*、用於遍歷資料結構的*迭代器*以及用於傳遞函數*的 lambda 運算式*。 通過使用這些語言和庫工具而不是原始指標,可以使程式更安全、更易於調試以及更易於理解和維護。 有關詳細資訊,請參閱[智慧指標](smart-pointers-modern-cpp.md)、[反覆運算器](../standard-library/iterators.md)和[Lambda 運算式](lambda-expressions-in-cpp.md)。

## <a name="in-this-section"></a>本節內容

- [原始指標](raw-pointers.md)
- [Const 和易失性指標](const-and-volatile-pointers.md)
- [新增運算子與刪除運算子](new-and-delete-operators.md)
- [智慧指標](smart-pointers-modern-cpp.md)
- [如何:建立和使用unique_ptr實體](how-to-create-and-use-unique-ptr-instances.md)
- [如何:建立及使用shared_ptr實體](how-to-create-and-use-shared-ptr-instances.md)
- [如何:建立與使用weak_ptr實體](how-to-create-and-use-weak-ptr-instances.md)
- [如何:建立與使用 CComPtr 與 CComQIPtr 實體](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>另請參閱

[迭代器](../standard-library/iterators.md)</br>
[Lambda 運算式](lambda-expressions-in-cpp.md)
