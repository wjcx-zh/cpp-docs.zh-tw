---
title: "如何：建立和使用 shared_ptr 執行個體 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 如何：建立和使用 shared_ptr 執行個體
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`shared_ptr` 型別是在 C\+\+ 標準程式庫中的一種智慧型指標，是為一個以上的擁有者可能必須管理物件在記憶體中的存留期之情節所設計。  在您初始化`shared_ptr` 後，您可以複製、 以函式引數的值傳送也可以將它賦值給其他 `shared_ptr` 執行個體。  所有執行個體都指向相同的物件，並對一「控制區塊」共用存取其參考計數的遞增和遞減，當新的 `shared_ptr` 加入，將會超出範圍或重設。  在參考計數達到零時，控制區塊會刪除記憶體資源和自己本身。  
  
 下圖顯示的是指向一記憶體位置的多個 `shared_ptr` 執行個體。  
  
 [![共用指標](../cpp/media/shared_ptr.png "shared\_ptr")](assetId:///9785ad08-31d8-411a-86a9-fb9cd9684c27)  
  
## 範例  
 可能的話，當記憶體資源第一次建立時，請使用 [make\_shared](../Topic/make_shared%20\(%3Cmemory%3E\).md) 函式建立 `shared_ptr` 。  `make_shared` 是例外狀況安全的。  它會使用相同的呼叫去配置控制區塊和資源的記憶體，因而降低建構的額外負荷。  如果您不使用 `make_shared`，則在將它傳遞給 `shared_ptr` 建構函式前，您必須先使用明確的新運算式建立物件。  下列範例顯示各種宣告和初始化 `shared_ptr` 及新物件的方式。  
  
 [!code-cpp[stl_smart_pointers#1](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]  
  
## 範例  
 下列範例顯示如何宣告和初始化採用已被另一個`shared_ptr`配置之物件共用擁有權的 `shared_ptr` 執行個體。  假設 `sp2` 是一個已初始化的 `shared_ptr`。  
  
 [!code-cpp[stl_smart_pointers#2](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]  
  
## 範例  
 當您使用複製項目的演算法時，`shared_ptr` 也適用於 Standard Template Library \(STL\) 容器。  您可以將 `shared_ptr` 中的項目包裝，然後將它複製到能夠辨識只要需要且不再需要即有效之基礎記憶體的其他容器中。  下列範例說明如何在向量中的 `shared_ptr` 執行個體運用 `replace_copy_if` 演算法。  
  
 [!code-cpp[stl_smart_pointers#4](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]  
  
## 範例  
 您可以使用 `dynamic_pointer_cast`、 `static_pointer_cast` 和 `const_pointer_cast` 轉換成 `shared_ptr`。  這些函式類似 `dynamic_cast`、 `static_cast` 和 `const_cast` 運算子。  下列範例顯示如何測試在基底類別的 `shared_ptr` 向量中每個項目的衍生型別，然後複製元素並顯示其相關資訊。  
  
 [!code-cpp[stl_smart_pointers#5](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]  
  
## 範例  
 您可以透過下列方式將 `shared_ptr` 傳遞至另一個函式：  
  
-   `shared_ptr` 的傳值。  這個呼叫複製建構函式、增加參考計數並且讓被呼叫端成為擁有者。  此作業有少量的額外負荷，也可能視您傳的 `shared_ptr` 物件多寡而變顯著。  當程式碼在呼叫端和被呼叫端之間的協定 \(隱含或明確\) 需要被呼叫端為擁有人時，請使用這個選項。  
  
-   `shared_ptr` 的傳參考或常數參考 。  在這種情況下，參考計數不會增加，因此只要呼叫端不超出範圍被呼叫端可以存取指標。  或者，接收者可以決定建立根據參考的 `shared_ptr` 進而成為共用的擁有者。  當呼叫端不了解被呼叫端或您必須傳 `shared_ptr` 且要基於效能考量要避免複製作業時，請使用這個選項。  
  
-   將基底指標或參考傳至基礎物件。  這可讓被呼叫端使用物件，但是並不讓它共用擁有權或擴充其存留期。  如果被呼叫端會從原始指標創建 `shared_ptr` ，則新 `shared_ptr` 與原始無關並且不控制基礎資源。  當呼叫端和被呼叫端之間的協定明確指定被呼叫端保留 `shared_ptr` 存留期的擁有權時，請使用這個選項。  
  
-   當您決定如何傳 `shared_ptr` 時，判斷被呼叫端是否必須共用基底資源的擁有權。  「Owner」是一個只要需要基礎資源就能使用它的物件或函式。  如果呼叫端必須確保被呼叫端可以擴充指標的存留期在其 \(函式\) 的存留期之外的，請使用第一個選項。  如果您不在乎被呼叫端是否擴充存留期，則傳參考並讓被呼叫端複製它。  
  
-   如果您必須允許 Helper 函式對基底指標的存取，並且您知道 Helper 函式將使用指標並在呼叫的函式傳回之前傳回，則此函式不需要共用基底指標的擁有權。  它只能存取在呼叫端的 `shared_ptr` 存留期內之指標。  在這種情況下，`shared_ptr` 傳參考、原始指標、或基礎物件的參考是安全的。  以這種方式提供一個小的效能優點，也可以協助您表達程式設計的意圖。  
  
-   在某些情況下，例如在 `std:vector<shared_ptr<T>>` 中，您可能必須將每個 `shared_ptr` 傳到 Lambda 運算式主體或具名函式物件。  如果 lambda 或函式不儲存指標，則傳 `shared_ptr` 參考以避免呼叫每個元素的複製建構函式。  
  
 [!CODE [stl_smart_pointers#6](../CodeSnippet/VS_Snippets_Cpp/stl_smart_pointers#6)]  
  
## 範例  
 下列範例顯示 `shared_ptr` 如何多載各種比較運算子以啟用 `shared_ptr` 執行個體所擁有之記憶體的指標比較。  
  
 [!code-cpp[stl_smart_pointers#3](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]  
  
## 請參閱  
 [智慧型指標](../cpp/smart-pointers-modern-cpp.md)