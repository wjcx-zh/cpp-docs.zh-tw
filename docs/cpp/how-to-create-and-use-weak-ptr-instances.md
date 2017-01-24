---
title: "如何：建立和使用 weak_ptr 執行個體 | Microsoft Docs"
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
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：建立和使用 weak_ptr 執行個體
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有時候，物件必須以存取 `shared_ptr` 基礎物件而不造成參考計數遞增的方式來儲存。  當 `shared_ptr` 執行個體之間有循環參考存在時，通常會發生這種情況。  
  
 最好的設計是盡可能避免共用指標擁有權。  不過，如果您必須擁有 `shared_ptr` 執行個體的共用擁有權，請避免在它們之間產生循環參考。  當循環參考無法避免，或者由於某種原因反而比較好時，請使用 `weak_ptr` 將另一個 `shared_ptr` 的參考指定給一個或多個擁有者。  使用 `weak_ptr`，可建立 `shared_ptr` 以聯結一組現有的相關執行個體，但是只有在基礎記憶體資源有效的情況下才有可能。  `weak_ptr` 本身不會參與參考計數，因此，它無法防止參考計數變成零。  不過，您可以使用 `weak_ptr`，嘗試取得用來初始化之 `shared_ptr` 的新複本。  如果記憶體已經刪除，會擲回 **bad\_weak\_ptr** 例外狀況。  如果記憶體仍然有效，新的共用指標會遞增參考計數，並保證只要 `shared_ptr` 變數保持在範圍中，記憶體就是有效。  
  
## 範例  
 下列程式碼範例示範使用 `weak_ptr` 確保正確刪除有循環相依性之物件的案例。  當您可以檢查這個範例，假設它是在考慮替代方案之後建立的。  `Controller` 物件表示電腦處理序的某些方面，這些物件會獨立運作。  每個控制器都必須可以隨時查詢其他控制器的狀態，而且每個控制器都包含此用途的私用 `vector<weak_ptr<Controller>>`。  每個向量包含循環參考，因此使用 `weak_ptr` 執行個體而不是 `shared_ptr`。  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
  **建立 Controller0**  
**建立 Controller1**  
**建立 Controller2**  
**建立 Controller3**  
**建立 Controller4**  
**push\_back to v\[0\]: 1**  
**push\_back to v\[0\]: 2**  
**push\_back to v\[0\]: 3**  
**push\_back to v\[0\]: 4**  
**push\_back to v\[1\]: 0**  
**push\_back to v\[1\]: 2**  
**push\_back to v\[1\]: 3**  
**push\_back to v\[1\]: 4**  
**push\_back to v\[2\]: 0**  
**push\_back to v\[2\]: 1**  
**push\_back to v\[2\]: 3**  
**push\_back to v\[2\]: 4**  
**push\_back to v\[3\]: 0**  
**push\_back to v\[3\]: 1**  
**push\_back to v\[3\]: 2**  
**push\_back to v\[3\]: 4**  
**push\_back to v\[4\]: 0**  
**push\_back to v\[4\]: 1**  
**push\_back to v\[4\]: 2**  
**push\_back to v\[4\]: 3**  
**use\_count \= 1**  
**狀態 1 \= On**  
**Status of 2 \= On**  
**Status of 3 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**Status of 2 \= On**  
**Status of 3 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**狀態 1 \= On**  
**Status of 3 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**狀態 1 \= On**  
**Status of 2 \= On**  
**Status of 4 \= On**  
**use\_count \= 1**  
**Status of 0 \= On**  
**狀態 1 \= On**  
**Status of 2 \= On**  
**Status of 3 \= On**  
**Destroying Controller0**  
**Destroying Controller1**  
**Destroying Controller2**  
**Destroying Controller3**  
**Destroying Controller4**  
**按任意鍵** 在此做個實驗，請將向量 `others` 修改為 `vector<shared_ptr<Controller>>`，然後在輸出中注意觀察，當 `TestRun` 傳回時並沒有叫用任何解構函式。  
  
## 請參閱  
 [智慧型指標](../cpp/smart-pointers-modern-cpp.md)