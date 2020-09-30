---
title: 智慧型指標 (新式 C++)
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 909ef870-904c-49b6-b8cd-e9d0b7dc9435
ms.openlocfilehash: e511cc513cdb35b06b976ce022c5e4edea35040b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500677"
---
# <a name="smart-pointers-modern-c"></a>智慧型指標 (新式 C++)

在新式 c + + 程式設計中，標準程式庫包含 *智慧型指標*，可用來協助確保程式沒有記憶體和資源流失，而且是例外狀況安全的。

## <a name="uses-for-smart-pointers"></a>智慧型指標的用途

智慧型指標是在 `std` 標頭檔的命名空間中定義 [\<memory>](../standard-library/memory.md) 。 這些是對 [RAII](./object-lifetime-and-resource-management-modern-cpp.md) 或資源取得的關鍵 *，就是初始化程式* 設計的用法。 這個慣用語主要目標是確保在初始化物件的同時會進行擷取資源，使建立物件的所有資源在一行程式碼中建立並且準備就緒。 實際上，RAII 的主要原則就是將任何堆積配置資源的擁有權 (例如，動態配置記憶體或系統物件控制代碼) 提供給含有刪除或釋放資源程式碼的解構函式，以及任何相關清除程式碼的堆疊配置物件。

大部分情況下，當您初始化原始指標或資源控制代碼以指向實際資源時，會立即將指標傳遞給智慧型指標。 在現代 C++ 中，原始指標只能用於極重視效能且擁有權不會混淆之有限範圍的小型程式碼區塊、迴圈或 Helper 函式。

下列範例將原始指標宣告與智慧型指標宣告做比較。

[!code-cpp[smart_pointers_intro#1](codesnippet/CPP/smart-pointers-modern-cpp_1.cpp)]

如範例所示，智慧型指標是在堆疊上宣告、並且以指向堆積配置物件的原始指標初始化的類別樣板。 智慧型指標在初始化後，就會擁有原始指標。 這表示智慧型指標會刪除原始指標指定的記憶體。 智慧型指標解構函式包含對 delete 的呼叫，而且因為智慧型指標是在堆疊上宣告，因此當智慧型指標超出範圍時，便會叫用其解構函式，即使例外狀況是從比堆疊更上方的位置擲回亦然。

使用熟悉的指標運算子 `->` 和 `*` (智慧型指標類別會進行多載以傳回封裝的原始指標) 存取封裝的指標。

C++ 智慧型指標慣用語與在 C# 等語言中建立物件的情形類似：您會建立物件，然後讓系統負責在適當時機將其刪除。 差別在於背景中沒有執行是沒有個別記憶體回收行程；記憶體是透過標準 C++ 範圍設定規則來管理，因此執行階段環境會更快速且更有效率。

> [!IMPORTANT]
> 請一律在不同的程式碼行上建立智慧型指標，絕不可在參數清單建立，如此可避免因某些參數清單配置規則，而發生無法預測的資源流失。

下列範例示範如何 `unique_ptr` 使用 c + + 標準程式庫中的智慧型指標類型，將指標封裝至大型物件。

[!code-cpp[smart_pointers_intro#2](codesnippet/CPP/smart-pointers-modern-cpp_2.cpp)]

下列範例示範使用智慧型指標的基本步驟。

1. 將智慧型指標宣告為自動 (區域) 變數。  (不使用 **`new`** `malloc` 智慧型指標本身的或運算式。 ) 

1. 在類型參數中，指定封裝指標的指向類型。

1. 將原始指標傳遞至 **`new`** 智慧型指標函式中的-ed 物件。 (某些公用程式函式或智慧型指標建構函式即可進行此步驟)。

1. 使用多載的 `->` 和 `*` 運算子來存取物件。

1. 讓智慧型指標刪除物件。

智慧型指標是針對在記憶體和效能兩方面都達到最大效率而設計。 例如，封裝的指標 `unique_ptr` 的唯一資料成員。 這表示 `unique_ptr` 與該指標有完全相同的大小，四個位元組或八個位元組。 使用智慧型指標多載的 * 和-> 運算子來存取封裝的指標，會比直接存取原始指標慢很多。

智慧型指標有自己的成員函式，可使用「點」標記法來存取。 例如，某些 c + + 標準程式庫智慧型指標具有重設成員函式，可釋放指標的擁有權。 當您要在智慧型指標超出範圍之前釋出智慧型指標所擁有的記憶體時，這將會很有用，如下列範例所示。

[!code-cpp[smart_pointers_intro#3](codesnippet/CPP/smart-pointers-modern-cpp_3.cpp)]

智慧型指標通常會提供直接存取其原始指標的方法。 C + + 標準程式庫智慧型指標具有 `get` 此用途的成員函式，且 `CComPtr` 具有公用 `p` 類別成員。 智慧型指標可讓您直接存取基礎指標，您可以用來在自己的程式碼管理記憶體，而且仍然可以將原始指標傳遞至不支援智慧型指標的程式碼。

[!code-cpp[smart_pointers_intro#4](codesnippet/CPP/smart-pointers-modern-cpp_4.cpp)]

## <a name="kinds-of-smart-pointers"></a>智慧型指標的種類

下列章節中將摘要說明可在 Windows 程式設計環境中使用的各種不同智慧型指標，並描述其使用時機。

### <a name="c-standard-library-smart-pointers"></a>C + + 標準程式庫智慧型指標

使用這些智慧型指標做為封裝純舊 C++ 物件 (POCO) 指標的首要選擇。

- `unique_ptr`<br/>
   只允許一個基礎指標的擁有者。 用做 POCO 的預設選項，除非您確信自己需要 `shared_ptr`。 可以移至新擁有者，但不可複製或共用。 替換已被取代的 `auto_ptr`。 與 `boost::scoped_ptr` 比較。 `unique_ptr` 很小且有效率;大小是一個指標，它支援從 c + + 標準程式庫集合快速插入和抓取的右值參考。 標頭檔：`<memory>`。 如需詳細資訊，請參閱 [如何：建立和使用 Unique_ptr 實例](how-to-create-and-use-unique-ptr-instances.md) 和 [unique_ptr 類別](../standard-library/unique-ptr-class.md)。

- `shared_ptr`<br/>
   參考計數的智慧型指標。 在您想要將原始指標指派給多個擁有者時使用，例如，當您從容器傳回指標的複本，但是想要保留原來的指標時。 原始指標只有在所有的 `shared_ptr` 擁有者都超出範圍或放棄擁有權之後，才會被刪除。 大小是兩個指標；一個針對物件，另一個則針對含有參考計數的共用控制區塊。 標頭檔：`<memory>`。 如需詳細資訊，請參閱 [如何：建立和使用 Shared_ptr 實例](how-to-create-and-use-shared-ptr-instances.md) 和 [shared_ptr 類別](../standard-library/shared-ptr-class.md)。

- `weak_ptr`<br/>
    與 `shared_ptr` 一起使用的特殊案例智慧型指標。 `weak_ptr` 可以讓您存取由一個或多個 `shared_ptr` 執行個體擁有的物件，但是不會參與參考計數。 當您想要觀察物件，但不需要物件保持運作時，即可使用。 在某些要中斷 `shared_ptr` 執行個體之間循環參考的情況下為必要項。 標頭檔：`<memory>`。 如需詳細資訊，請參閱 [如何：建立和使用 Weak_ptr 實例](how-to-create-and-use-weak-ptr-instances.md) 和 [weak_ptr 類別](../standard-library/weak-ptr-class.md)。

### <a name="smart-pointers-for-com-objects-classic-windows-programming"></a>COM 物件的智慧型指標 (傳統的 Windows 程式設計) 

當您使用 COM 物件時，請將介面指標包裝在適當的智慧型指標類型中。 Active Template Library (ATL) 會定義數個各種用途的智慧型指標。 您也可以使用 `_com_ptr_t` 智慧型指標類型，編譯器會在從 .tlb 檔案建立包裝函式類別時使用這個類型。 當您不想要包含 ATL 標頭檔時，這是最佳選擇。

[CComPtr 類別](../atl/reference/ccomptr-class.md)<br/>
除非無法使用 ATL，否則請使用這種方式。 使用 `AddRef` 和 `Release` 方法執行參考計數。 如需詳細資訊，請參閱 [如何：建立和使用 CComPtr 和 CComQIPtr 實例](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)。

[CComQIPtr 類別](../atl/reference/ccomqiptr-class.md)<br/>
與`CComPtr` 類似，但是有提供在 COM 物件上呼叫 `QueryInterface` 的簡化語法。 如需詳細資訊，請參閱 [如何：建立和使用 CComPtr 和 CComQIPtr 實例](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)。

[CComHeapPtr 類別](../atl/reference/ccomheapptr-class.md)<br/>
使用 `CoTaskMemFree` 釋放記憶體之物件的智慧型指標。

[CComGITPtr 類別](../atl/reference/ccomgitptr-class.md)<br/>
由全域介面資料表 (GIT) 取得之介面的智慧型指標。

[_com_ptr_t 類別](com-ptr-t-class.md)<br/>
在功能上與 `CComQIPtr` 類似，但是不相依於 ATL 標頭。

### <a name="atl-smart-pointers-for-poco-objects"></a>POCO 物件的 ATL 智慧型指標

除了 COM 物件的智慧型指標之外，ATL 也會針對純舊的 c + + 物件定義智慧型指標和智慧型指標集合， (POCO) 。 在傳統的 Windows 程式設計中，這些類型是 c + + 標準程式庫集合的有用替代方案，特別是在不需要程式碼可攜性時，或當您不想要混用 c + + 標準程式庫和 ATL 的程式設計模型時。

[CAutoPtr 類別](../atl/reference/cautoptr-class.md)<br/>
藉由傳送複本上的擁有權以強制唯一擁有權的智慧型指標。 類似已被取代的 `std::auto_ptr` 類別。

[CHeapPtr 類別](../atl/reference/cheapptr-class.md)<br/>
使用 C [malloc](../c-runtime-library/reference/malloc.md) 函數所配置之物件的智慧型指標。

[CAutoVectorPtr 類別](../atl/reference/cautovectorptr-class.md)<br/>
用於以 `new[]` 所配置之陣列的智慧型指標。

[CAutoPtrArray 類別](../atl/reference/cautoptrarray-class.md)<br/>
將 `CAutoPtr` 項目陣列封裝的類別。

[CAutoPtrList 類別](../atl/reference/cautoptrlist-class.md)<br/>
將方法封裝以操作 `CAutoPtr` 節點清單的類別。

## <a name="see-also"></a>另請參閱

[指標](pointers-cpp.md)<br/>
[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)
