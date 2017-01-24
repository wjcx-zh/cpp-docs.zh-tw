---
title: "集合 | Microsoft Docs"
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
  - "陣列樣板"
  - "陣列 [C++], 類別"
  - "集合類別, 關於集合類別"
  - "集合類別, 陣列"
  - "集合類別, 清單"
  - "集合類別, 對應"
  - "集合類別, MFC"
  - "集合類別, 圖案"
  - "集合類別, 樣板架構"
  - "集合, 關於集合"
  - "MFC 集合類別"
  - "MFC, 集合"
  - "圖案"
  - "圖案, 集合"
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫提供集合類別管理物件群組。  這些類別有兩種類型：  
  
-   [從 C\+\+ 樣板建立的集合類別。](#_core_the_template.2d.based_collection_classes)  
  
-   [非從樣板建立的集合類別。](#_core_the_collection_classes_not_based_on_templates)  
  
> [!NOTE]
>  如果您的程式碼已經使用非樣板集合類別，可以繼續使用它們。  如果您撰寫新的型別安全集合為您的資料型別分類，我們建議您使用較新的樣板類別。  
  
##  <a name="_core_collection_shapes"></a> 集合形狀  
 集合類別 Draw 為它的形狀與由其項目的型別。  圖案參考組織並儲存物件集合的方式。  MFC 提供三個基本圖案集合:清單、陣列和對應 \(也稱為字典\)。  您可以選擇最適合您的特定程式設計問題的圖案集合。  
  
 提供三個集合圖案中的每一本主題稍後的簡短說明。  若要比較圖案的功能可協助您決定要提供程式最適合使用，請參閱 [選擇集合類別的建議](../mfc/recommendations-for-choosing-a-collection-class.md)。  
  
-   List  
  
     清單類別提供項目清單的指令，索引清單，實作為雙向連結串列。  清單中有「開頭」與「結尾」，以及加入或移除項目的開頭或結尾或插入或刪除項目在中間，非常快速地。  
  
-   陣列  
  
     陣列類別提供動態大小的，已排序和整數索引的陣列。  
  
-   對應 \(也稱為字典\)  
  
     導覽是相關聯金鑰的物件與值物件的集合。  
  
##  <a name="_core_the_template.2d.based_collection_classes"></a> 樣板架構集合類別  
 最簡單的方法實作包含任何型別的物件的型別安全集合是使用其中一個 MFC 樣板類別。  這兩個類別的範例，請參閱 MFC [收集](../top/visual-cpp-samples.md)範例。  
  
 下表列出MFC範文為基底的並行集合類別。  
  
### 集合樣板類別  
  
|集合內容|陣列|清單|對應|  
|----------|--------|--------|--------|  
|任何型別之物件的集合。|`CArray`|`CList`|`CMap`|  
|指標的集合對任何型別的物件|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|  
  
##  <a name="_core_the_collection_classes_not_based_on_templates"></a> 根據樣板中的集合類別。  
 如果您的應用程式已經使用MFC非樣板類別，可以繼續使用它們。  不過，對於新集合，我們建議您使用樣板類別。  下表列出不是根據範本的 MFC 集合類別。  
  
### 非樣板集合類別  
  
|陣列|清單|對應|  
|--------|--------|--------|  
|`CObArray`|`CObList`|`CMapPtrToWord`|  
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|  
|`CDWordArray`|`CStringList`|`CMapStringToOb`|  
|`CPtrArray`||`CMapStringToPtr`|  
|`CStringArray`||`CMapStringToString`|  
|`CWordArray`||`CMapWordToOb`|  
|`CUIntArray`||`CMapWordToPtr`|  
  
 MFC 集合在 [選擇集合類別的建議](../mfc/recommendations-for-choosing-a-collection-class.md) 類別的資料表的特性說明 MFC 集合類別會根據這些特性 \(除了圖案之外\)：  
  
-   類別會使用 C\+\+ 樣板與否  
  
-   儲存在集合中的項目是否可序列化  
  
-   儲存在集合中的項目是否可用於診斷傾印  
  
-   這個值是否為安全型別。  
  
### 您想要執行甚麼工作？  
  
#### 一般集合類別工作  
  
-   [選擇集合類別的建議](../mfc/recommendations-for-choosing-a-collection-class.md)  
  
-   [如何：建立類型安全集合](../mfc/how-to-make-a-type-safe-collection.md)  
  
-   [建立堆疊和佇列集合](../mfc/creating-stack-and-queue-collections.md)  
  
-   [CArray::Add](../Topic/CArray::Add.md)  
  
#### 樣板架構集合類別  
  
-   [樣板架構類別](../mfc/template-based-classes.md)  
  
#### 存取集合成員 \(樣本基底或非樣本基底\)  
  
-   [存取集合的所有成員](../mfc/accessing-all-members-of-a-collection.md)  
  
-   [刪除 CObject 集合中的所有物件](../mfc/deleting-all-objects-in-a-cobject-collection.md)  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)   
 [一般 MFC 主題](../mfc/general-mfc-topics.md)