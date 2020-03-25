---
title: 編譯器錯誤 C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 93b6e414f26c56702a1c7ac12863cbcd5063b570
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177491"
---
# <a name="compiler-error-c2558"></a>編譯器錯誤 C2558

'identifier' : 沒有可用的複製建構函式或是複製建構函式宣告為 'explicit'

複製建構函式 (Copy Constructor) 從另一個相同類型的物件上初始化物件 （它會建立物件的複本）。如果您未定義任何的函式，編譯器會產生預設的複製函數。

### <a name="to-fix-this-error"></a>修正此錯誤

1. 當嘗試複製的類別所擁有的複製建構函式為 `private` 時，就可能會發生這個問題。 在大部分情況下，不應複製具有 `private` 複製建構函式的類別。 一般程式設計技術會宣告一個 `private` 複製建構函式，來防止直接使用類別。 該類別單獨使用可能毫無用處，或需要另一個類別才能正確運作。

   如果您判斷使用具有 `private` 複製建構函式的類別是安全的，則從具有 `private` 建構函式的類別上衍生新的類別，並在新類別中提供 `public` 或 `protected` 複製建構函式使用。 使用這個衍生類別取代原本的。

1. 當嘗試複製的類別所擁有的複製建構函式為 explicit 時，就可能會發生這個問題。 將複製建構函式宣告為 `explicit`，可防止將類別的物件傳遞至函式，或將類別的物件從函式傳回。 如需明確的函式的詳細資訊，請參閱[使用者定義型別轉換](../../cpp/user-defined-type-conversions-cpp.md)。

1. 若嘗試複製的類別執行個體使用複製建構函式宣告了 `const`，但該建構函式未採用 `const` 傳址參數，就可能會發生這個問題。 請宣告具有 `const` 類型參考而不是非常數類型參考的複製建構函式。
