---
title: "物件存留期和資源管理 (現代 C++) | Microsoft Docs"
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
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 物件存留期和資源管理 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不同於 Managed 語言， C\+\+ 沒有記憶體回收 \(GC\)，版本不會自動使用記憶體資源，程式執行。  在 C\+\+ 中，資源管理員會直接與物件存留期相關。  本文件說明會影響在 C\+\+ 物件的存留期和如何處理它的因素。  
  
 主要因為它無法處理非記憶體資源， C\+\+ 沒有 GC。  與的只判斷解構函式在 C\+\+ 可能平均處理記憶體和非記憶體資源。  GC 也有其他問題，例如更高的額外負荷在記憶體和 CPU 使用量和位置。  但是，全球無法透過智慧最佳化會降低的基本問題。  
  
## 概念  
 一件重要的事情在物件存留期管理方面是封裝其使用物件不需要知道資源該物件擁有，或如何釋放它們，甚至是擁有任何資源。  它只能終結物件。  C\+\+ 核心語言設計保證物件終結在正確時間，也就是，因為區塊結尾，在建構反向。  在物件終結時，它的基底和成員以特殊的順序被終結。除非您做類似，新的堆積配置或位置的特殊事項語言自動終結物件。例如， [智慧型指標](../cpp/smart-pointers-modern-cpp.md) \(如 `unique_ptr` 和 `shared_ptr`和 Standard Template Library \(STL\) 容器像 `vector`，封裝 `new`\/`delete` 和 `new[]`\/`delete[]` 物件中，有解構函式。  因此使用智慧型指標和 STL 容器是很重要的。  
  
 另一個重要概念在存留期管理方面:解構函式。  解構函式封裝資源版本。\(常用的助憶鍵是 RRID，資源版本是解構函式\)。資源是從「系統」取得並稍後必須傳回回收的動作。記憶體是最常見的資源，不過，也有檔案、通訊、材質和其他非記憶體資源。擁有資源表示您可以使用，在需要時，還必須釋放它，會在完成時。在物件終結時，其解構函式來釋放其資源。  
  
 最後的概念是 DAG \(維持非循環圖\)。擁有權結構在程式的表單 DAG。  物件可以擁有本身，不僅不可能，本質上也無意義。  但是，兩個物件可以共用第三個物件的擁有權。數種連結可能會在如下的 DAG:是 B 的成員 \(B 擁有 A\)， C\# 的 `vector<D>` \(C\# 擁有每個 D 項目\)，電子儲存 `shared_ptr<F>` \(E 與其他物件共用 F 擁有權，可能\)，依此類推。只要沒有循環，並在 DAG 的每個連結都由具有解構函式的物件表示 \(而不是原始指標、控制代碼，或其他機制\)，然後資源遺漏是不可能的，因為語言防止它們。  資源釋放，在不再需要之後，不用，記憶體回收行程執行。  存留期追蹤是堆疊範圍、基底、成員和相關問題的額外負荷可用，並可以 `shared_ptr`的。  
  
### 基於堆積的存留期  
 對於堆積物件存留期，請使用 [智慧型指標](../cpp/smart-pointers-modern-cpp.md)。  使用 `shared_ptr` 和 `make_shared` 做為預設指標和配置器。  使用 `weak_ptr` 中斷循環，進行快取，並觀察物件，而不會影響或假設任何有關其存留期。  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 為唯一的擁有權使用 `unique_ptr` ，例如，在 *pimpl* 慣用語。\(請參閱[編譯時期封裝的 Pimpl](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)\)。讓 `unique_ptr` 主要目標任何明確的 `new` 運算式。  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 您可以為非擁有權和檢視使用原始指標。  非主控指標可能連接下列，不過它不能遺漏。  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 在需要時最佳化效能，您可能必須使用 *封裝* 擁有指標和明確呼叫 Delete。  範例為您實作自己的低階資料結構。  
  
### 以堆疊為基礎的存留期  
 在現代 C\+\+， *以堆疊為基礎的範圍* 是一項強大的撰寫強固的程式碼，因為它會結合自動 *堆疊存留期* ，而資料與有效存留期追蹤的 *成員存留期* 基本上免於額外負荷。  尤其是您與原始指標時，堆積物件存留期要求工作手動管理，也可以是資源遺漏和效率低落來源。  考慮這段程式碼，示範以堆疊為基礎的範圍:  
  
```cpp  
class widget {  
private:  
  gadget g;   // lifetime automatically tied to enclosing object  
public:  
  void draw();  
};  
  
void functionUsingWidget () {  
  widget w;   // lifetime automatically tied to enclosing scope  
              // constructs w, including the w.g gadget member  
  …  
  w.draw();  
  …  
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
  
```  
  
 謹慎使用靜態存留期 \(全域靜態函式，區域靜態\)，因為問題可能會出現。  當全域物件的建構函式擲回例外狀況，會發生什麼事?  一般而言，應用程式錯誤會很難偵錯的方法。  建構順序為靜態物件的存留期會有問題，而不是並行安全的。  不僅是物件建構問題，解構函式順序可能會很複雜，尤其是多型是包含的地方。  即使您的物件或變數不是多型的，不複雜建構\/解構定序，仍有安全執行緒並行問題。  多執行緒的應用程式無法安全地修改靜態物件的資料未含有執行緒區域儲存區、資源鎖定和其他特殊預防措施。  
  
## 請參閱  
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)