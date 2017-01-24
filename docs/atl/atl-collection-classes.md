---
title: "ATL 集合類別 | Microsoft Docs"
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
  - "集合類別"
  - "集合類別, 關於集合類別"
  - "集合類別, 選擇"
  - "ConstructElements 函式"
  - "CTraits 類別"
  - "DestructElements 函式"
  - "SerializeElements 函式"
  - "traits 類別"
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 集合類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 用來儲存和存取資料提供許多類別。  類別 \(Class\) 您決定使用取決於許多因素，包括:  
  
-   要儲存的資料量。  
  
-   效率至存取資料的效能  
  
-   存取資料由索引或索引鍵  
  
-   資料排列  
  
-   個人喜好設定  
  
## 小型集合類別。  
 ATL 在處理提供下列陣列類別少部分的物件。  不過，這些類別會受到和內部設計為使用 ATL。  建議您不要在程式中使用它們。  
  
|類別|資料存放區的型別|  
|--------|--------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|實作處理的陣列類別少部分的物件。|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|實作處理的對應類別少部分的物件。|  
  
## 一般用途的集合類別。  
 在一般用途的集合類別，遵循類別實作陣列、清單和對應類別並提供:  
  
|類別|資料存放區的型別|  
|--------|--------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|實作一個陣列。|  
|[CAtlList](../atl/reference/catllist-class.md)|實作一個清單。|  
|[CAtlMap](../atl/reference/catlmap-class.md)|實作一個對應結構，，讓資料都可以使用索引鍵或值的參考。|  
|[CRBMap](../atl/reference/crbmap-class.md)|使用紅色粗體演算法，實作的對應結構。|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|實作一個紅色粗體 multimapping 的結構。|  
  
 這些類別可截獲許多程式設計錯誤，以及使用偵錯組建，，但為了效能和示範說明，這些檢查在正式版本組建不會執行。  
  
## 特定的集合類別。  
 特殊化集合類別來管理記憶體指標和介面指標也提供:  
  
|類別|用途|  
|--------|--------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|以建構一個陣列智慧型指標時，提供有用的方法。|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|以建構清單智慧型指標時，提供有用的方法。|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|儲存 `IUnknown` 指標和是設計用來做為參數 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 樣板類別。|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|以建構清單堆積指標時，提供有用的方法。|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|以建構一個陣列 COM 介面指標時，提供有用的方法。|  
|[CInterfaceList](../atl/reference/cinterfacelist-class.md)|以建構清單 COM 介面指標時，提供有用的方法。|  
  
## 選取集合類別  
 每個可用的集合類別提供不同的效能特性，如下表所示。  
  
-   資料行 2 和 3 描述每個的順序和存取特性。  在資料表中， 「訂購」一詞表示項目插入和刪除作業的順序會決定其集合中的順序;不代表項目在其內容排序。  「索引」一詞表示集合中的項目可由整數索引擷取，就像在一般陣列的項目。  
  
-   資料行 4 和 5 描述每個的效能。  在需要很多插入集合中的應用程式，插入速度可能特別重要，至於其他應用程式，查閱速度更重要。  
  
-   資料行 6 描述每個圖案是否允許重複的項目。  
  
-   指定集合類別作業的效能是以所需時間之間的關係完成作業和項目集合中的物件數目。  需要以線性方式將時間的作業，當項目擴充數目是描述為 O\(n\) 演算法。  相反地，需要減少加入的作業，當項目擴充數目是描述為 O \(log n\) 演算法。  因此，就效能而言， O \(log n\) 演算法的好處是 O\(n\) 多對演算法，當項目數目增加。  
  
### 集合形狀功能  
  
|圖案|排序?|索引?|插入<br /><br /> 項目|搜尋<br /><br /> 指定的項目。|重複<br /><br /> 項目?|  
|--------|---------|---------|---------------|-------------------|----------------|  
|List|是|否|快速 \(常數時間\)|降低 O\(n\)|是|  
|陣列|是|由 int \(常數時間\)|降低 O\(n\)，不過如果插入在結束，在這種情況下，常數時間情況下|降低 O\(n\)|是|  
|對應|否|依據索引鍵 \(常數時間\)|快速 \(常數時間\)|快速 \(常數時間\)|沒有 \(機碼\) 是 \(值\)|  
|紅色粗體導覽|為 \(根據索引鍵\)|依據索引鍵 O \(log n\)|快速 O \(log n\)|快速 O \(log n\)|否|  
|紅色粗體 Multimap|為 \(根據索引鍵\)|依據索引鍵 O \(log n\) \(多值每個索引鍵\)|快速 O \(log n\)|快速 O \(log n\)|是 \(多值每個索引鍵\)|  
  
## 使用 CTraits 物件  
 在 ATL 集合類別可用來儲存各種使用者定義的資料型別，可以覆寫重要函式來比較可能會很有用。  使用類別， CTraits 達到此效果。  
  
 CTraits 類別類似，不過，比彈性， MFC 集合類別的 Helper 函式，請參閱 [集合類別 Helper](../mfc/reference/collection-class-helpers.md) 以取得詳細資訊。  
  
 當建構您的集合類別時，您可以指定 CTraits 類別的選項。  這個類別包含要執行的比較作業 \(例如，在呼叫其他方法組成集合類別的程式碼。  例如，在中，如果您的清單物件包含您的使用者定義結構，您可能想要重新定義相等測試只會比對某些成員變數。  如此一來，清單物件的 Find 方法所操作的更有用的方式。  
  
## 範例  
  
### 程式碼  
 [!code-cpp[NVC_ATL_Utilities#112](../atl/codesnippet/CPP/atl-collection-classes_1.cpp)]  
  
## 註解  
 如需 CTraits 類別清單，請參閱 [集合類別。](../atl/collection-classes.md)。  
  
 下圖顯示 CTraits 類別的類別階層架構。  
  
 ![集合類別的特性階層架構](../atl/media/vctraitscollectionclasseshierarchy.png "vcTraitsCollectionClassesHierarchy")  
  
## 集合類別範例分類  
 下列範例示範集合類別:  
  
-   [MMXSwarm 範例](../top/visual-cpp-samples.md)  
  
-   [DynamicConsumer 範例](../top/visual-cpp-samples.md)  
  
-   [UpdatePV 範例](../top/visual-cpp-samples.md)  
  
-   [Marquee 範例](../top/visual-cpp-samples.md)  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [集合類別](../atl/collection-classes.md)