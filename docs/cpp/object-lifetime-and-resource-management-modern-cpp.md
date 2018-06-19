---
title: 物件存留期和資源管理 （現代 c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 634bef1bf9d2d3128497a1321631ca8665fed144
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423492"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>物件存留期和資源管理 (現代 C++)
不同於 Managed 語言，C++ 沒有記憶體回收 (GC)，其會在程式執行時自動釋出不再使用的記憶體資源。 在 C++ 中，資源管理與物件存留期有直接關係。 本文件說明影響 C++ 之物件存留期的因素，以及其管理方式。  
  
 C++ 沒有 GC 的主要原因是它不處理非記憶體資源。 只有像 C++ 中的那些具決定性的解構函式能均衡處理記憶體和非記憶體資源。 GC 也有其他問題，例如在記憶體和 CPU 消耗量與位置的額外負荷更高。 但是，普遍性這個基本問題並無法透過明智的最佳化過程來降低。  
  
## <a name="concepts"></a>概念  
 物件存留期管理上一件很重要的事是封裝，無論誰在使用物件，並不需要知道該物件擁有哪些資源、如何釋放資源，或是否擁有任何資源。 它只需終結物件。 C++ 核心語言的設計可保證物件在正確時間 (即區塊結束時) 依照建構的反向順序終結。 在物件終結時，它的基底和成員會以特殊的順序終結。  除非您做了類似堆積配置或新配置的特殊事項，否則語言會自動終結物件。  例如，[智慧型指標](../cpp/smart-pointers-modern-cpp.md)像`unique_ptr`和`shared_ptr`，如同 c + + 標準程式庫容器和`vector`，封裝`new` / `delete`和`new[]` /`delete[]`中的物件，其具有解構函式。 這就是為什麼它是很重要，使用智慧型指標和 c + + 標準程式庫容器。  
  
 另一個存留期管理的重要概念：解構函式。 解構函式封裝資源釋放。  (常用的助憶鍵是 RRID，資源釋放是解構函式)。資源是從「系統」取得，且稍後必須還回的事物。  記憶體是最常見的資源，不過也有檔案、通訊端、材質和其他非記憶體資源。 「擁有」資源表示您可以在需要時使用它，但用完時必須釋放它。  在物件終結時，其解構函式會釋放其擁有的資源。  
  
 最終概念是 DAG (導向非循環圖)。  程式中的擁有權結構會形成 DAG。 物件無法擁有本身，而且不僅不可能，本質上也無意義。 但是，兩個物件可以共用第三個物件的擁有權。  DAG 中可能會有數種連結：A 是 B 的成員 (B 擁有 A)，C 儲存 `vector<D>` (C 擁有每個 D 項目)，E 儲存 `shared_ptr<F>` (E 可能與其他物件共用 F 的擁有權)，依此類推。  只要沒有循環，而且 DAG 中的每個連結都由具有解構函式的物件來代表 (而不是原始指標、控制代碼或其他機制)，就不可能發生資源流失，因為語言防止這種情況產生。 當不再需要資源時，就會釋放資源，完全不需執行記憶體回收。 存留期追蹤對於堆疊範圍、基底、成員和相關案例的無負荷的，對於 `shared_ptr` 而言也不昂貴。  
  
### <a name="heap-based-lifetime"></a>堆疊式存留期  
 對於堆積物件存留期、 使用[智慧型指標](../cpp/smart-pointers-modern-cpp.md)。 使用 `shared_ptr` 和 `make_shared` 做為預設指標和配置器。 使用 `weak_ptr` 中斷循環、進行快取，並觀察物件，完全不會影響或負擔任何存留期相關事項。  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
  
```  
  
 使用`unique_ptr`針對唯一擁有權，例如，在*pimpl*慣用語。 (請參閱[編譯時間封裝的 Pimpl](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)。)讓 `unique_ptr` 成為所有明確 `new` 運算式的主要目標。  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 您可以針對非擁有權和觀測使用原始指標。 非主控指標可能依附，但不能流失。  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
  
```  
  
 當需要效能最佳化時，您可能必須使用*封裝良好*擁有指標和刪除的明確呼叫。 範例為實作自己的低階資料結構。  
  
### <a name="stack-based-lifetime"></a>堆疊式存留期  
 現代 c + +*堆疊式範圍*是功能強大的方式寫入強固的程式碼，因為它會結合自動*堆疊存留期*和*資料成員存留期*具有高效率：存留期追蹤基本上沒有的額外負荷。 堆積物件存留期需要用心的手動管理，因此可能成為資源流失和效率低落的來源，尤其在使用原始指標時。 考慮這段程式碼，示範堆疊式範圍：  
  
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
    // ...
    w.draw();  
    // ...
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
```  
  
 謹慎使用靜態存留期 (全域靜態函式，區域靜態)，不然可能會出現問題。 當全域物件的建構函式擲回例外狀況時，會發生什麼事？ 一般而言，應用程式錯誤某方面來說很難進行偵錯。 建構順序對於靜態存留期物件而言反而會造成問題，且不是並行安全。 不僅物件建構有問題，解構函式順序可能會很複雜，尤其是涉及多型之處。 即使您的物件或變數不是多型，且沒有複雜的建構/解構定序，仍會有安全執行緒並行問題。 沒有靜態執行緒區域儲存區、資源鎖定和其他特殊預防措施，多執行緒的應用程式就無法安全地修改靜態物件的資料。  
  
## <a name="see-also"></a>另請參閱  
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)