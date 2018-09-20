---
title: Safe_cast 轉換標記法和簡介&lt;&gt; |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88e8165bde08b65b4f078c4b48863c2088132fca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427858"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Safe_cast 轉換標記法和簡介&lt;&gt;

轉換通知已從 Managed Extensions for c + + Visual c + +。

修改現有的結構是不同且更困難的體驗，相較於設計初始的結構。 有較少的自由度，與解決方案通常會理想的重整和功能是可行的作法指定現有的結構化相依性之間折衷。

語言擴充功能是另一個範例。 回 1990年年代初期為物件指定的程式設計變得很重要的範例中，c + + 中的型別安全向下轉換功能的需求將成為按。 向下轉型就是使用者明確轉換的基底類別的指標或指標參考或衍生類別的參考。 向下轉換需要明確轉換。 原因是基底類別指標的實際型別是執行階段; 的一環編譯器因此無法檢查它。 或者，若要重新敘述，，向下轉型的設備，就像虛擬函式呼叫，需要某種形式的動態解析。 這會引發兩個問題：

- 為什麼應該向下轉型是物件導向的範例中的必要？ 不足的虛擬函式機制？ 也就是為什麼無法其中一個宣告若不需要向下轉型 （或任何類型的轉型） 是設計失敗？

- 為什麼應該的向下轉型的支援是 c + + 中的問題？ 畢竟，它不是物件導向語言，例如 Smalltalk 中的問題 (或之後，Java 和 C#)？ 什麼是關於 c + + 可支援向下轉型的設備困難？

虛擬函式類型的一系列代表一般型別相關演算法。 （我們不會考慮其不支援 ISO c + + 中，但可用於 CLR 程式設計和代表有趣的設計替代方案的介面。） 這在沒有宣告公用介面 （虛擬函式） 和一組代表應用程式中的實際系列類型具體衍生類別的抽象基底類別的類別階層通常表示該系列的設計網域。

A`Light`階層中的電腦產生影像 (CGI) 應用程式定義域，比方說，例如具有通用的屬性`color`， `intensity`， `position`， `on`， `off`，依此類推。 其中一個可以控制數個號誌，而不必擔心焦點、 定向光線、 非方向性燈 （想像的 sun） 或也許靶門光線的特定的燈號是否使用通用介面。 在此情況下，向下的轉型為特定 light-型別執行其虛擬介面是不必要的。 在生產環境中，不過，速度是不可或缺。 其中一個可能會向下轉型，並明確地叫用每個方法如果這麼做可以執行呼叫的內嵌執行，而不是使用虛擬的機制。

因此，在 c + + 向下轉型的其中一個原因是隱藏的顯著的提升，在執行階段效能代價虛擬的機制。 （請注意，此手動最佳化的自動化研究的活躍議題。 不過，很難解決比取代明確使用`register`或`inline`關鍵字。)

向下轉型的第二個理由脫離多型的雙重本質。 多型的比喻被分成一組被動和動態的表單。

虛擬引動過程 （和向下轉型的設備） 代表動態使用多型： 其中一個項目執行動作的程式執行該特定執行個體的基底類別指標的實際類型為基礎。

不過，在衍生的類別物件指派給它的基底類別指標，是被動的一種多型;它使用多型做為傳輸機制。 這是主要使用`Object`，例如預先一般 CLR 程式設計中。 使用被動，通常選擇傳輸和儲存體的基底類別指標就會提供太抽象的介面。 `Object`例如，提供透過其介面; 大約五個方法更具體的行為必須明確向下轉型。 例如，如果我們想要調整聚光燈的角度或減弱關閉的速率，會有明確地向下轉換。 一系列子型別內的虛擬介面實務上無法的所有可能的方法，其許多的子系的超集，因此向下轉型的設備一律需物件導向語言中。

如果向下轉型安全設施需要在物件導向語言，然後為什麼需要 c + + 這麼長的時間中加入一個？ 問題在於如何讓指標的執行階段類型資訊可用。 虛擬函式，在執行階段資訊中設定兩個部分，編譯器：

- 類別物件包含其他的虛擬資料表成員指標 (在開頭或結尾類別物件，這本身有個有趣的故事) 項目，定址適當的虛擬資料表。 例如，spotlight 物件位址的 spotlight 虛擬資料表、 定向光線、 定向光線的虛擬資料表等等

- 每個虛擬函式都有相關聯固定位置，在資料表中，並叫用的實際執行個體由儲存在資料表中的位址。 例如，虛擬`Light`解構函式可能會與位置 0，相關聯`Color`與位置 1，依此類推。 這是效益不具彈性的策略，因為它在編譯時期設定且代表最少的額外負荷。

此問題，然後是如何將類型資訊提供給指標而不需要變更 c + + 指標的大小，加上第二個位址或直接將某種類型的編碼方式。 這不是可接受的程式設計人員 （和程式），決定不使用物件導向開發架構-這仍是最主要的使用者社群。 另一個可能性是導入的多型類別類型的特殊指標，但這可能會造成混淆，而且難以混合兩者，特別是使用指標算術問題。 它也不會維護每個指標關聯其目前相關聯的型別，並以動態方式更新它的執行階段資料表可接受。

問題則是一組使用者社群有不同，但合法程式設計正當性。 解決方案必須為兩個的社群，讓每一個抱負不僅交互操作的能力之間取得折衷。 這表示提供任一端的解決方案時可能不可行，而且實作的方案是不怎麼完美。 多型類別的定義為中心的實際解決方法： 為多型類別是包含虛擬函式。 多型的類別支援動態型別安全向下轉型。 這可解決維護--指標-做為位址的問題，因為所有的多型類別包含的其他指標成員及其相關聯的虛擬資料表。 因此，相關聯的型別資訊中，可以儲存在擴充的虛擬資料表結構中。 類型安全向下轉型的成本 （幾乎） 當地語系化為功能的使用者。

類型安全向下轉型的下一個問題是它的語法。 因為它是轉型，原始提案的 ISO c + + 委員會來使用的未裝飾型別轉換語法，如此範例所示：

```
spot = ( SpotLight* ) plight;
```

但這已被拒絕由該委員會因為它並不允許使用者控制轉換的成本。 動態型別安全向下轉型是否相同的語法為先前不安全，但靜態轉型標記法，則它會變成替代，而且使用者沒有不必要和成本可能太高時，隱藏執行階段額外負荷的能力。

一般情況下，在 c + +，總是有一個機制可以用來隱藏編譯器支援的功能。 比方說，我們可以關閉虛擬機制使用類別範圍運算子 (`Box::rotate(angle)`) 或叫用虛擬方法，透過類別物件 （而非指標或參考該類別的）。 此第二個隱藏項目不需要的語言，但是品質的實作問題，類似於表單的宣告中的暫存資料表的建構隱藏項目：

```
// compilers are free to optimize away the temporary
X x = X::X( 10 );
```

因此提案拍攝回做進一步的考量，已考量數個替代的標記法，並帶回至委員會是表單的 (`?type`)，這表示其未定-也就是動態的本質。 此舉可讓使用者能夠切換-靜態或動態-兩種形式，但沒有人是值得高興。 因此，它會回到繪圖面板。 第三個和成功的標記法是現在標準`dynamic_cast<type>`，這一組的四個新樣式轉換標記法一般化。

ISO-c + +`dynamic_cast`會傳回`0`套用不當的指標類型，且會擲回時`std::bad_cast`套用至參考型別時的例外狀況。 在 Managed Extensions for c + +，套用`dynamic_cast`受管理的參考類型 （因為其指標表示法），一定會傳回`0`。 `__try_cast<type>` 例外狀況擲回的變體導入成類比`dynamic_cast`，只不過它會擲回`System::InvalidCastException`若轉換失敗。

```
public __gc class ItemVerb;
public __gc class ItemVerbCollection {
public:
   ItemVerb *EnsureVerbArray() [] {
      return __try_cast<ItemVerb *[]>
         (verbList->ToArray(__typeof(ItemVerb *)));
   }
};
```

在新語法中，`__try_cast`已重新轉換為`safe_cast`。 以下是相同的程式碼片段，在新語法中：

```
public ref class ItemVerb;
public ref class ItemVerbCollection {
public:
   array<ItemVerb^>^ EnsureVerbArray() {
      return safe_cast<array<ItemVerb^>^>
         ( verbList->ToArray( ItemVerb::typeid ));
   }
};
```

在 managed 世界中，務必以供驗證的程式碼，藉由限制程式設計人員能夠在離開程式碼無法驗證的方式中的類型之間進行轉換。 這是由新語法的動態程式設計範例的重要層面。 因此，舊式的轉型執行個體會在內部重新轉換為執行階段轉換的範例：

```
// internally recast into the
// equivalent safe_cast expression above
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );
```

相反地，多型提供了主動與被動模式，因此就有時必須執行向下轉型只是用來存取子類型的非虛擬的 API。 這可能是，比方說，與類別的成員，要位址任何類型階層架構 （被動多型做為傳輸機制） 內，但特定程式內容中的實際執行個體已知的。 在此情況下，執行階段檢查可以是轉換的無法接受的額外負荷。 如果新的語法是用來做為受管理的系統程式設計語言，它必須提供一些方法，允許編譯時期的 (也就是靜態) 向下轉型。 這就是為什麼應用程式的`static_cast`標記法可以維持編譯時間向下轉型：

```
// ok: cast performed at compile-time.
// No run-time check for type correctness
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));
```

問題在於無法保證，程式設計人員進行`static_cast`正確且本來用意良好; 也就是沒有任何方法，以強制受管理的程式碼，以進行驗證。 這是多緊急的考量下比在原生的動態程式開發架構，但不足夠系統程式設計語言不允許使用者能夠切換靜態和執行階段轉換內。

沒有效能陷阱和陷阱，在新語法中，不過。 在原生程式設計中，並無差別效能之間的舊樣式型別轉換標記法和新樣式`static_cast`標記法。 但在新語法中，舊式的轉換標記法的費用會比使用新樣式`static_cast`標記法。 原因是編譯器會在內部將舊式的標記法，則會擲回例外狀況的執行階段檢查到的使用。 此外，它也會變更程式碼的執行設定檔因為發生無法攔截的例外狀況，將應用程式下： 可能是明智的做法，但相同的錯誤不會導致該例外狀況，如果`static_cast`標記法所使用。 其中一個可能會認為這有助於 prod 成使用新樣式標記的使用者。 但只有在它失敗時否則，它會導致執行速度大幅沒有可見的原因、 了解使用舊式的標記法的程式類似於下列的 C 程式設計人員陷阱：

```
// pitfall # 1:
// initialization can remove a temporary class object,
// assignment cannot
Matrix m;
m = another_matrix;

// pitfall # 2: declaration of class objects far from their use
Matrix m( 2000, 2000 ), n( 2000, 2000 );
if ( ! mumble ) return;
```

## <a name="see-also"></a>另請參閱

[一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[使用 /clr 進行 C-style 轉換 (C + + /cli CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)<br/>
[safe_cast](../windows/safe-cast-cpp-component-extensions.md)