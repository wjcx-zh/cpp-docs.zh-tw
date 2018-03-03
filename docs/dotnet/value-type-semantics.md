---
title: "值的類型語意 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- interior_ptr keyword [C++]
- virtual functions, value types
- inheritance, value types
- pinning pointers
- pin_ptr keyword [C++]
- __pin keyword
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 21a7d6bcba2fca3fddd6f5e234663d6791398f5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="value-type-semantics"></a>實值類型語意
實值類型語意已從 Managed Extensions for c + + Visual c + +。  
  
 以下是用於 Managed Extensions for c + + 規格的標準簡單實值類型：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 在 Managed Extensions，我們可以有四種語法變化，實值類型 （其中 2 和 3 的表單是相同語意）：  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## <a name="invoking-inherited-virtual-methods"></a>叫用繼承虛擬方法  
 `Form (1)`不標準值物件，而且它是合理充分了解，除了當有人嘗試叫用的繼承虛擬方法時，例如`ToString()`。 例如:   
  
```  
v.ToString(); // error!  
```  
  
 若要叫用此方法，因為它不會在 覆寫`V`，編譯器必須能夠存取基底類別的相關聯的虛擬資料表。 實值型別是沒有相關聯的指標至其虛擬資料表 (vptr) 的狀態中儲存體，因為這需要`v`會進行 boxed 處理。 在 Managed Extensions 語言設計中，隱含 boxing 不支援，但必須明確地指定程式設計人員，在  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 此設計背後的主要動機是教學： 基礎機制必須顯示程式設計人員，讓其了解的 '成本' 未提供值型別中的執行個體。 已`V`要包含的執行個體`ToString`，boxing 不是必要的。  
  
 明確 boxing 物件，但不是本身，boxing 的基礎成本的語彙複雜度會移除在新語法中：  
  
```  
v.ToString(); // new syntax  
```  
  
 代價是可能會產生誤解，類別設計工具中未提供明確的執行個體的成本有關`ToString`方法內`V`。 偏好的隱含 boxing 的原因是通常是一個類別設計工具，雖然有無限的數量的使用者，他會沒有自由地修改`V`消除可能很繁重的明確方塊。  
  
 這是要判斷是否要提供的覆寫執行個體的準則`ToString`內值的頻率和它的使用位置，應該是類別。 如果呼叫很少，是當然其定義的好處。 同樣地，如果呼叫非高效能的應用程式區域中，將它加入會也不適當地加入至應用程式的一般效能。 或者，可以保持追蹤控制代碼為 boxed 值，並透過該控制代碼呼叫不會要求 boxing。  
  
## <a name="there-is-no-longer-a-value-class-default-constructor"></a>不再值類別預設建構函式  
 值型別之間受管理的擴充功能和新語法的另一個差異是支援的預設建構函式中移除。 這是因為有時候可以在其中 CLR 建立之值型別的執行個體而不叫用相關聯的預設建構函式執行期間。 也就是管理擴充功能下嘗試，以支援實值類型中的預設建構函式可能實際上不保證。 指定缺乏保證，它被認為比較適合將一併刪除支援，而不是具決定性其應用程式中。  
  
 這不是一開始可能看起來如下的錯誤。 這是因為實值類型的每個物件會自動去除 （也就是每個型別會初始化為其預設值）。 如此一來，一定會未定義的本機執行個體成員。 就這個意義而言，定義 trivial 預設建構函式的能力遺失其實不會遺失所有-，事實上時由 CLR 執行更有效率。  
  
 此問題時，受管理的擴充功能的使用者定義的非 trivial 預設建構函式。 這對於沒有對應至新語法。 建構函式中的程式碼必須是移轉至必須明確叫用由使用者命名的初始設定方法。  
  
 新語法中的實值類型物件的宣告則未變更。 這個缺點是實值型別並不令人滿意包裝原生類型的原因如下：  
  
-   沒有任何支援的實值類型內的解構函式。 也就是說，沒有任何方法可以自動化的一組物件的存留期結束時所觸發的動作。  
  
-   原生類別可以包含只在 managed 類型，然後會在原生堆積上配置的指標。  
  
 我們想要包裝在實值類型，而非參考類型以避免重複堆積配置的小型原生類別： 原生堆積以保存原生型別，與 CLR 堆積來保存 managed 包裝函式。 包裝原生類別實值類型可讓您避免受管理的堆積，但不提供任何方法來自動執行的原生堆積記憶體回收。 參考型別是在其中包裝非一般的原生類別只使其受管理的類型。  
  
## <a name="interior-pointers"></a>內部指標  
 `Form (2)`和`Form (3)`上方可以解決幾乎這個世界或下一個 （也就是任何 managed 或原生） 中任何項目。 因此，比方說，下列所有條件中允許受管理的擴充功能：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
V *pv = 0;  // Form (2)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0;  // Form (4)  
  
R* r;  
  
pv = &v;            // address a value type on the stack  
pv = __nogc new V;  // address a value type on native heap  
pv = pvgc;          // we are not sure what this addresses  
pv = pvbx;          // address a boxed value type on managed heap  
pv = &r->vr;        // an interior pointer to value type within a  
                    //    reference type on the managed heap  
```  
  
 因此，`V*`可以解決在本機的區塊內的位置，因此可以懸空在全域範圍內原生堆積 （例如，若其定址之物件已刪除），在 CLR 堆積 （且因此將會追蹤是否應該重新放置在記憶體回收期間），並參考 （內部指標，因為這個呼叫時，也會明確地追蹤） 到 CLR 堆積上物件的內部。  
  
 在 Managed Extensions，沒有任何方法可以區分出的原生的層面`V*`; 也就是說，它會被視為在其內含處理它定址的物件或子物件，在 managed 堆積上的可能性。  
  
 在新語法中，實值類型指標納入兩種類型： `V*`，這是僅包含非 CLR 堆積位置，以及內部指標， `interior_ptr<V>`，允許但不需要在受管理的堆積內的位址。  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 `Form (2)`和`Form (3)`管理延伸模組的對應到`interior_ptr<V>`。 `Form (4)`是追蹤控制代碼。 針對整個 managed 堆積中具有已 box 的物件。 它就會轉譯成新的語法中`V^`，  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 所有對應至新的語法中的內部指標的 Managed Extensions 中的下列宣告。 (它們是實值類型內`System`命名空間。)  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 內建型別不會考慮 managed 型別，雖然它們執行做為別名中的型別`System`命名空間。 因此下列對應成立之間受管理的擴充功能和新的語法：  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 轉譯時`V*`在現有的程式中，最保守的策略是一律將它以`interior_ptr<V>`。 這是如何處理受管理的擴充功能下。 在新語法中，程式設計人員的選項為未受管理的堆積位址限制實值類型，藉由指定`V*`而不是內部指標。 如果轉譯程式，您可以執行所有其使用可轉移結束，並確定沒有指派的位址是 managed 堆積中，然後讓它為`V*`是正常的。  
  
## <a name="pinning-pointers"></a>Pin 指標  
 記憶體回收行程可能會選擇性地移動通常是在壓縮階段位於堆積內的不同位置到 CLR 堆積的物件。 此移動不追蹤控制代碼，追蹤參考和內部指標以透明的方式更新這些實體的問題。 不過，如果使用者已傳遞物件位址以外的執行階段環境到 CLR 堆積上時，此動作將會有問題。 在此情況下，動態移動物件很可能會導致執行階段失敗。 豁免的物件，例如從正在移動，我們必須在本機將其釘選到其範圍外部使用的位置。  
  
 在 Managed Extensions， *pin 指標*宣告限定名稱的指標宣告`__pin`關鍵字。 從 Managed Extensions 規格稍微修改範例如下：  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // ...  
};  
```  
  
 在新的語言設計中，是以類似的內部指標的語法來宣告 pin 指標。  
  
```  
ref struct H  
{  
public:  
   int j;  
};  
  
int main()  
{  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
  
   // ...  
}  
```  
  
 在新語法的 pin 指標是特殊的內部指標。 仍 pin 指標原始條件約束。 例如，它不能做為參數或方法的傳回型別它可以宣告本機物件上。 一些其他條件約束，不過，已加入新的語法。  
  
 Pin 指標的預設值是`nullptr`，而非`0`。 A`pin_ptr<>`無法初始化或指派`0`。 所有的工作分派`0`現有程式碼中需要變更以`nullptr`。  
  
 解決整個物件，如下列範例取自 Managed Extensions 規格允許受管理的擴充功能的 pin 指標：  
  
```  
__gc class G {  
public:  
   void incr(int* pi) { pi += 1; }  
};  
__gc struct H { int j; };  
void f( G * g ) {  
   H __pin * pH = new H;     
   g->incr(& pH -> j);     
};  
```  
  
 在新語法中，釘選整個物件來傳回`new`不支援運算式。 而是需要釘選內部成員的位址。 例如，套用至物件的  
  
```  
ref class G {  
public:  
   void incr(int* pi) { *pi += 1; }  
};  
ref struct H { int j; };  
void f( G^ g ) {  
   H ^ph = gcnew H;  
   Console::WriteLine(ph->j);  
   pin_ptr<int> pj = &ph->j;  
   g->incr(  pj );  
   Console::WriteLine(ph->j);  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [實值類型和它們的行為 (C + + /CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [類別和結構](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior_ptr (C + + /CLI)](../windows/interior-ptr-cpp-cli.md)   
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)