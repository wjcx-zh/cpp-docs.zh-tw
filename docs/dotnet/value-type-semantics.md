---
title: "實值類型語意 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__pin 關鍵字"
  - "繼承, 實值類型"
  - "interior_ptr 關鍵字 [C++]"
  - "pin_ptr 關鍵字 [C++]"
  - "Pin 指標"
  - "虛擬函式, 實值類型"
ms.assetid: 7f065589-ad25-4850-baf1-985142e35e52
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 實值類型語意
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，實值型別 \(Value Type\) 語意已變更。  
  
 下列是在 Managed Extensions for C\+\+ 規格中所使用的標準簡單實值型別：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
```  
  
 在 Managed Extensions 中，一種實值型別可以擁有四種語法變數 \(其中形式 2 和 3 的語意相同\)：  
  
```  
V v = { 0 };       // Form (1)  
V *pv = 0;         // Form (2) an implicit form of (3)  
V __gc *pvgc = 0;  // Form (3)  
__box V* pvbx = 0; // Form (4) must be local   
```  
  
## 叫用繼承的虛擬方法  
 `Form (1)` 是標準值物件，而且已獲得適當的充分暸解，但是當某人嘗試叫用如 `ToString()` 之類之繼承的虛擬方法時例外。  例如：  
  
```  
v.ToString(); // error!  
```  
  
 如果要叫用此方法，由於並未在 `V` 中覆寫此方法，因此編譯器必須擁有相關基底類別之虛擬資料表的存取權。  因為實值型別是缺少虛擬資料表之相關指標 \(vptr\) 的目前狀態中 \(in\-state\) 儲存體，因此會要求 Box 處理 `v`。  在 Managed Extensions 語言設計中，未支援隱含的 Boxing，但是必須由程式設計人員明確指定，如下所示  
  
```  
__box( v )->ToString(); // Managed Extensions: note the arrow  
```  
  
 此設計背後的主要動機具備教學意義：程式設計人員必須能夠看見基礎機制，使其了解不在實值型別中提供執行個體的「代價」。  如果 `V` 包含 `ToString` 的執行個體，就不一定需要 Boxing。  
  
 在新語法中，會移除明確 Boxing 物件的語彙複雜性，但不會移除 Boxing 本身的基礎代價：  
  
```  
v.ToString(); // new syntax  
```  
  
 但是至於在 `V` 中未提供 `ToString` 方法的明確執行個體的代價，則是可能會誤導類別設計工具。  慣用隱含 Boxing 的原因在於，通常類別設計工具只有一個，使用者卻有無限多個，如果沒有一個使用者可以自由修改 `V`，就可以消除可能很繁重的明確 Box。  
  
 判定是否在實值類別中提供 `ToString` 之覆寫執行個體的準則，是執行個體的使用頻率和位置。  如果很少呼叫，當然在定義中就沒有什麼優勢。  同樣地，如果在應用程式的非效能區域中呼叫，加入執行個體也不會適當地加入至應用程式的一般效能。  此外，可以將追蹤處理代碼保持為 Boxed 值，則透過該處理代碼所做的呼叫就不需要 Boxing。  
  
## 不再有實值類別預設建構函式  
 Managed Extensions 和新語法之間的另一項實值型別差異，則是後者已移除預設建構函式的支援。  原因是在執行期間，有時 CLR 可以不需要叫用相關的預設建構函式，就直接建立實值型別的執行個體。  也就是說，在 Managed Extensions 中，嘗試在實值型別中支援預設建構函式實際上無法獲得保證。  如果缺乏保證，那麼徹底刪除支援似乎比在應用程式中不具決定性來好。  
  
 這並不像一開始看到的那麼糟。  這是因為會自動去除實值型別的每個物件 \(亦即每個型別都會初始化為其預設值\)。  因此，一定會定義本機執行個體的成員。  就這點看來，無法定義一般預設建構函式真的一點都不算是損失，而且事實上，當由 CLR 執行時還更有效率。  
  
 問題是當 Managed Extensions 的使用者定義非一般預設建構函式時。  這一點並未對應至新語法。  建構函式中的程式碼將需要遷移至具名初始化方法，而此方法之後需要由使用者明確叫用。  
  
 新語法中的實值型別物件宣告則未變更。  此項目的缺點是，實值型別基於下列理由並未符合原生型別包裝的要求：  
  
-   在實值型別中沒有解構函式 \(Destructor\) 的支援。  也就是說，無法自動化物件存留期結束時所觸發的一組動作。  
  
-   原生類別只能當做指標內含於 Managed 型別中，此指標稍後會配置在原生堆積 \(Heap\) 上。  
  
 我們想要將小的原生類別包裝於實值型別而非參考型別中，以避免重複堆積配置：原生堆積是用來存放原生型別，而 CLR 堆積是用來存放 Managed 包裝函式。  將原生類別包裝於實值型別中可以避免 Managed 堆積，但是無法自動化原生堆積記憶體的回收。  參考型別是唯一可在其中包裝非一般原生類別的 Managed 型別。  
  
## 內部指標  
 上述的 `Form (2)` 和 `Form (3)` 幾乎可以處理目前和以後的任何項目 \(亦即任何 Managed 或原生項目\)。  例如，因此在 Managed Extensions 中允許下列所有項目：  
  
```  
__value struct V { int i; };  
__gc struct R { V vr; };  
  
V v = { 0 };  // Form (1)  
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
  
 所以，`V*` 可以處理下列範圍內的位址：在區域區塊 \(因此可以依附\)、在全域範圍、在原生堆積中 \(例如，如果已刪除所處理的物件\)、在 CLR 堆積中 \(如果應該在記憶體回收期間遷移，因此應會追蹤\)，以及在 CLR 堆積的參考物件內部 \(如果呼叫，也會透明地追蹤內部指標\)。  
  
 在 Managed Extensions 中，無法區隔 `V*` 的原生部分，也就是說，將原生部分視為內含物，因而處理在 Managed 堆積上為物件或子物件定址的可能性。  
  
 在新語法中，實值型別指標分成兩種型別：限制在非 CLR 堆積位置的 `V*`，以及允許但是不需要 Managed 堆積中位址的內部指標 `interior_ptr<V>`。  
  
```  
// may not address within managed heap   
V *pv = 0;   
  
// may or may not address within managed heap  
interior_ptr<V> pvgc = nullptr;   
```  
  
 Managed Extensions 的 `Form (2)` 和 `Form (3)` 對應至 `interior_ptr<V>`。  `Form (4)` 是追蹤控制代碼。  它會處理已在 Managed 堆積中 Box 的整個物件。  在新語法中會轉譯為 `V^`。  
  
```  
V^ pvbx = nullptr; // __box V* pvbx = 0;    
```  
  
 Managed Extensions 中的下列宣告全部都會對應至新語法中的內部指標 \(這些內部指標是 `System` 命名空間中的實值型別\)。  
  
```  
Int32 *pi;   // => interior_ptr<Int32> pi;  
Boolean *pb; // => interior_ptr<Boolean> pb;  
E *pe;       // => interior_ptr<E> pe; // Enumeration  
```  
  
 雖然內建型別的確是當做 `System` 命名空間中的型別別名，但卻未被視為 Managed 型別。  因此下列對應會在 Managed Extensions 和新語法之間保持為真：  
  
```  
int * pi;     // => int* pi;  
int __gc * pi2; // => interior_ptr<int> pi2;  
```  
  
 轉譯現有程式中的 `V*` 時，最穩健的策略就是永遠將它變成 `interior_ptr<V>`。  這是在 Managed Extensions 中的處理方式。  在新語法中，程式設計人員可以選擇指定 `V*` 而非內部指標，藉此將實值型別限制為 Unmanaged 堆積位址。  如果轉譯程式時，可以為所有程式使用進行轉移終結，並且能夠確定沒有指派位址位於 Managed 堆積中，那麼保留為 `V*` 不會有問題。  
  
## Pin 指標  
 記憶體回收行程可以選擇將常駐於 CLR 堆積中的物件移動至堆積中的其他位置，而這通常是在壓縮階段進行。  這項移動對於追蹤控制代碼、追蹤參考以及透明地更新這些實體的內部指標而言都不是問題。  但是如果在執行階段環境以外，使用者已在 CLR 堆積上傳遞物件位址，這項移動就會造成問題。  在這種情況下，短暫移動物件可能會引起執行階段錯誤。  若要避免移動這類物件，必須針對物件外部使用的範圍，將物件區域性地 Pin 在位置上。  
  
 在 Managed Extensions 中，會使用 `__pin` 關鍵字限定指標宣告，藉以宣告「*Pin 指標*」\(Pinning Pointer\)。  下列是從 Managed Extensions 規格稍做修改的範例：  
  
```  
__gc struct H { int j; };  
  
int main()   
{  
   H * h = new H;  
   int __pin * k = & h -> j;  
  
   // …  
};  
```  
  
 在新的語言設計中，是使用類似內部指標的語法宣告 Pin 指標。  
  
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
  
   // …  
}  
```  
  
 新語法中的 Pin 指標是特殊的內部指標。  Pin 指標仍具有原本的條件約束。  例如，不能當做參數使用，也不能當做方法的傳回型別，只能在區域物件 \(Local Object\) 上宣告。  不過在新語法中還增加了一些其他條件約束。  
  
 Pin 指標的預設值是 `nullptr`，而不是 `0`。  `pin_ptr<>` 不能被指派或是初始化為 `0`。  需要將現有程式碼中的所有 `0` 的指派都變更為 `nullptr`。  
  
 Managed Extensions 中的 Pin 指標允許定址完整物件，如下列來自 Managed Extensions 規格的範例所示：  
  
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
  
 在新語法中，不支援 Pin 由 `new` 運算式所傳回的完整物件。  反而需要 Pin 內部成員的位址。  例如：  
  
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
  
## 請參閱  
 [實值類型和行為 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Classes and Structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)   
 [pin\_ptr \(C\+\+\/CLI\)](../windows/pin-ptr-cpp-cli.md)