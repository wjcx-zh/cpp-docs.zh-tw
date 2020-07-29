---
title: 編譯器錯誤 C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 2504b42f49ccb040f676f0aead8f243d33c7dd1a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207741"
---
# <a name="compiler-error-c2558"></a>編譯器錯誤 C2558

'identifier' : 沒有可用的複製建構函式或是複製建構函式宣告為 'explicit'

複製建構函式 (Copy Constructor) 從另一個相同類型的物件上初始化物件  （它會建立物件的複本）。如果您未定義任何的函式，編譯器會產生預設的複製函數。

### <a name="to-fix-this-error"></a>若要修正這個錯誤

1. 當嘗試複製的類別，其複製的「建立程式」為時，可能會發生此問題 **`private`** 。 在大部分情況下， **`private`** 不應複製具有複製程式的類別。 常見的程式設計技術會宣告複製的函式 **`private`** ，以防止直接使用類別。 該類別單獨使用可能毫無用處，或需要另一個類別才能正確運作。

   如果您判斷可以安全地使用具有複製程式化的類別 **`private`** ，請從具有此函式的類別衍生新的類別， **`private`** 並 **`public`** **`protected`** 在新的類別中提供或複製的函式。 使用這個衍生類別取代原本的。

1. 當嘗試複製的類別擁有明確的複製建構函式時，可能會發生這個問題。 將複製的函式宣告為， **`explicit`** 可防止在函式之間傳遞/傳回類別的物件。 如需明確的函式的詳細資訊，請參閱[使用者定義型別轉換](../../cpp/user-defined-type-conversions-cpp.md)。

1. 嘗試 **`const`** 使用未採用參考參數的複製程式來複製所宣告的類別實例時，可能會發生此問題 **`const`** 。 **`const`** 請使用類型參考（而不是非 const 類型參考）宣告您的複製函數。
