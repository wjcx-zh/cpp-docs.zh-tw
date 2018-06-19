---
title: 轉換通知和簡介的 safe_cast&lt; &gt; |Microsoft 文件
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
ms.openlocfilehash: 6b9432b40099f9893d7fd270faf5375646fb0493
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111636"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>轉換通知和 safe_cast 的簡介&lt;&gt;
轉型的表示法已從 Managed Extensions for c + + Visual c + +。  
  
 修改現有的結構是不同且更加困難的體驗，相較於設計初始的結構。 有較少的自由度，而解決方案往往理想的重整以及什麼是可行的作法指定現有結構的相依性之間的折衷。  
  
 語言擴充功能是另一個範例。 在早期 1990年年代為物件指定的方向程式設計變得很重要的開發架構，需要在 c + + 型別安全向下轉換功能會變成按。 向下轉型就是使用者明確轉換的基底類別的指標或指標參考或衍生類別的參考。 向下轉型需要明確轉換。 原因是基底類別指標的實際型別是執行階段則層面編譯器因此無法檢查它。 或者，您也可以重新潤飾一下，，向下轉型的功能，就好像是虛擬函式呼叫，它需要某種形式的動態解析。 這會引發兩個問題：  
  
-   為什麼應該向下轉型是必要的物件導向開發架構？ 沒有足夠的虛擬函式機制？ 也就是為什麼無法其中一個宣告若不需要在向下轉型 （或任何類型的轉型） 是設計失敗？  
  
-   支援的向下轉型為什麼要在 c + + 中的問題？ 在所有情況下，它並不是問題等 Smalltalk 的物件導向語言中 (或之後，Java 和 C#)？ 什麼是關於 c + + 支援向下轉型的設備困難？  
  
 虛擬函式，表示一系列型別共同的型別相關演算法。 （我們不會考慮的介面，ISO c + + 中不支援但可用於 CLR 程式設計和代表有趣的設計替代方案。） 這在沒有宣告通用介面 （虛擬函式） 以及一組代表應用程式中的實際系列型別具體衍生類別的抽象基底類別的類別階層架構通常表示該系列的設計網域。  
  
 A`Light`階層中的電腦產生圖像 (CGI) 應用程式定義域，比方說，例如具有通用屬性`color`， `intensity`， `position`， `on`， `off`，依此類推。 其中一個可以控制數個號誌，不必擔心精選、 方向燈、 非方向光線 （sun 想像，） 或可能靶門光線的特定的燈號是否使用通用介面。 在此情況下，向下的轉型為特定淺-型別以執行其虛擬介面是不必要的。 在實際執行環境中，不過，速度是不可或缺。 其中一個可能會向下轉型，以及明確叫用每個方法，就像這樣做可以執行呼叫的內嵌執行，而不是使用虛擬的機制。  
  
 因此，若要在 c + + 向下轉型的其中一個原因是隱藏虛擬機制以執行階段效能顯著提升。 （請注意，此手動最佳化的 automation 作用中區域的參考資料。 不過，很難解決比取代明確使用`register`或`inline`關鍵字。)  
  
 若要向下轉型的第二個原因脫離多型的雙重本質。 想到多型的其中一種方式被分割成被動和動態表單的組。  
  
 虛擬引動過程 （和向下轉型的設備） 代表動態使用多型： 其中一個執行動作的基底類別指標，該特定執行個體中執行程式的實際類型為基礎。  
  
 不過，在衍生的類別物件指派給它的基底類別指標，是一種多型; 的被動形式它使用多型，做為傳輸機制。 這是主要使用`Object`，例如，預先泛型 CLR 程式設計中。 以被動方式使用基底類別指標通常選擇傳輸與儲存區會提供太抽象的基礎介面。 `Object`例如，提供透過介面; 大約五種方法任何其他特定的行為需要明確向下轉型。 例如，如果我們想要調整的角度，我們精選或它的速率，我們必須向下轉型明確。 一系列子型別內的虛擬介面實務上無法的所有可能的方法，其許多的子系的超集，因此向下轉型的設備一律需要物件導向語言中。  
  
 如果向下轉型的安全功能需要在物件導向語言中，為何沒有 c + + 這麼久，新增一則？ 問題在於如何讓指標的執行階段類型資訊的使用中。 虛擬函式，在執行階段資訊是設定在兩個部分，編譯器：  
  
-   類別物件包含其他的虛擬資料表成員指標 (在開頭或結尾與類別物件的有本身的有趣的歷程記錄) 可解決適當的虛擬資料表。 精選物件，例如地址精選虛擬資料表，方向燈、 方向燈虛擬資料表等等  
  
-   每個虛擬函式都具有相關聯固定位置，在資料表中，並叫用的實際執行個體由儲存在資料表中的位址。 例如，虛擬`Light`解構函式可能插槽 0 中，與相關聯`Color`與插槽 1，依此類推。 這是效益卻往往缺乏彈性的策略，因為它設定在編譯時期，並且代表最低負擔。  
  
 此問題，然後是如何將類型資訊提供給指標而不需要變更 c + + 指標的大小，加入第二個位址，或是直接加入 某種類型的編碼方式。 這並不是可接受這些程式設計人員 （或程式），而決定使用的物件導向架構 」-這仍然是主要的使用者社群。 另一個可能性是引入特殊多型類別類型的指標，但這可能會造成混淆，而且難以混合兩者，特別是使用指標算術問題。 它也不會維護每個指標關聯其目前相關聯的類型，並以動態方式更新它的執行階段資料表可接受。  
  
 問題則是一組使用者社群有不同但合法程式的目標。 必須是兩個社群，讓每一個其雖然不僅交互操作的能力之間取得折衷方案。 這表示，任一端所提供的解決方案可能是不可行而實作的方案小於完美。 多型類別定義為中心的實際解決方法： 多型類別是包含虛擬函式。 多型類別支援動態類型安全向下轉型。 這樣可以解決維護-指標-作為-位址問題，因為所有的多型類別都包含該成員額外的指標至其相關聯的虛擬資料表。 相關聯的類型資訊，因此，可以儲存在擴充的虛擬資料表結構。 型別安全向下轉型的成本 （幾乎） 當地語系化為功能的使用者。  
  
 型別安全向下轉型的下一個問題是它的語法。 因為它是型別轉換，ISO c + + 至原始的提案使用未修飾的轉換語法，如此範例所示：  
  
```  
spot = ( SpotLight* ) plight;  
```  
  
 但這已被拒絕由該委員會因為它並不允許使用者控制轉換的成本。 如果動態類型安全向下轉型會具有相同的語法為先前不安全，但靜態轉型的表示法，則它會變成替代，而且使用者無法抑制執行階段額外負荷，不必要且成本可能太高時。  
  
 一般情況下，在 c + +，有一定是一種機制可以用來抑制編譯器支援的功能。 例如，我們可以關閉虛擬機制使用類別範圍運算子 (`Box::rotate(angle)`) 或由叫用虛擬方法，透過類別物件 （而非指標或參考該類別）。 抑制程式語言不需要，但是品質實作問題，類似於表單的宣告中的暫存建構的隱藏項目：  
  
```  
// compilers are free to optimize away the temporary  
X x = X::X( 10 );  
```  
  
 因此提案拍攝回做進一步的考量，已考量幾個替代的標記法，並帶回至委員會是表單的 (`?type`)，來表示其源自-也就是動態的本質。 這讓使用者能夠為靜態或動態的兩個形式之間切換但沒有人太滿意。 所以回到否定。 第三個和成功的表示法是非負數現在標準`dynamic_cast<type>`，這一組的四個新樣式轉換標記法一般化。  
  
 ISO-c + +`dynamic_cast`傳回`0`套用至不適當的指標類型，並擲回`std::bad_cast`時套用至參考類型的例外狀況。 在 Managed Extensions for c + +，套用`dynamic_cast`受管理的參考類型 （因為它的指標表示），一律傳回`0`。 `__try_cast<type>` 擲回的例外狀況導入成類比`dynamic_cast`，只不過它會擲回`System::InvalidCastException`若轉換失敗。  
  
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
  
 在新語法中，`__try_cast`已重新轉換為`safe_cast`。 在新語法中，以下是相同的程式碼片段：  
  
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
  
 在 managed 世界中，請務必允許透過限制的程式設計人員的能力，離開程式碼無法驗證的方法中的型別之間的轉換來驗證的程式碼。 這是由新語法的動態程式設計範例的重要層面。 因此，舊樣式轉換的執行個體會在內部重新轉換為執行階段轉換的範例：  
  
```  
// internally recast into the   
// equivalent safe_cast expression above  
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );   
```  
  
 相反地，因為多型提供了主動與被動模式，所以有時執行向下轉型就能夠存取子類型的非虛擬應用程式開發介面所需。 這可能會發生，比方說，與類別的成員，要位址任何型別階層 （被動多型做為傳輸機制） 內，但其已知的特定程式內容中的實際執行個體。 在此情況下，執行階段檢查可以是轉換的無法接受的額外負荷。 如果新的語法是用來做為程式設計語言的受管理系統，它必須提供編譯時期，允許某些方法 (也就是靜態) 向下轉型。 這就是為什麼的應用程式`static_cast`標記法可以維持編譯時期向下轉型：  
  
```  
// ok: cast performed at compile-time.   
// No run-time check for type correctness  
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));  
```  
  
 問題的原因是沒有方法可以保證進行程式設計人員`static_cast`正確且本意良好，但; 也就是沒有方法強制為可驗證的 managed 程式碼。 這是底下動態程式設計開發架構比在原生、 更緊急問題，但不足夠程式設計語言，讓使用者切換靜態和執行階段轉換的能力系統內。  
  
 不過會產生效能設陷和新語法中的錯誤。 在原生程式設計中，沒有無差異效能舊樣式轉型的表示法將新樣式`static_cast`標記法。 但是在新語法中，舊樣式轉型的表示法是非負數費用會比使用新樣式的`static_cast`標記法。 原因是編譯器在內部轉換成擲回例外狀況的執行階段檢查的舊式標記法使用。 此外，它也會變更程式碼的執行設定檔，因為發生無法攔截的例外狀況，讓應用程式-可能是個明智地，但相同的錯誤不會導致該例外狀況，如果`static_cast`標記法所使用。 其中一個可能會認為這可協助使用者使用新樣式的標記法的生產環境。 但只有時就會失敗;否則，它會導致執行速度會明顯沒有可見的原因，了解使用舊樣式的標記法的程式類似於下列的 C 程式設計人員困境：  
  
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
 [一般的語言變更 (C + + /CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [使用 /clr 進行 C-style 轉換 (C + + /CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)