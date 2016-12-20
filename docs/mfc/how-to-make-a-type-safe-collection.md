---
title: "如何：建立類型安全集合 | Microsoft Docs"
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
  - "集合類別, 衍生自非樣板"
  - "集合類別, 樣板架構"
  - "集合類別, 類型安全"
  - "序列化 [C++], 集合類別"
  - "SerializeElements 函式"
  - "序列化集合類別項目"
  - "類型安全的集合"
ms.assetid: 7230b2db-4283-4083-b098-eb231bf5b89e
caps.latest.revision: 10
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：建立類型安全集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何進行資料型別的型別安全集合。  主題包括：  
  
-   [請改用型別安全的樣板類別](#_core_using_template.2d.based_classes_for_type_safety)  
  
-   [實作協助函式](#_core_implementing_helper_functions)  
  
-   [使用非樣板集合類別](#_core_using_nontemplate_collection_classes)  
  
 MFC 程式庫提供以 C\+\+ 樣板的預先定義型別安全集合。  因為他們是範例所以這些類別可提供在用於這個非樣板類別和易用性，不是模型模擬和其他額外的工作相關的型別安全。  MFC [收集](../top/visual-cpp-samples.md) 範例示範在 MFC 應用程式樣板架構集合類別。  一般而言，請使用這些類別撰寫新的設定程式碼時。  
  
##  <a name="_core_using_template.2d.based_classes_for_type_safety"></a> 請改用型別安全的範本類別  
  
#### 若要使用範本類別  
  
1.  宣告集合中的型別變數。  例如：  
  
     [!code-cpp[NVC_MFCCollections#7](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_1.cpp)]  
  
2.  呼叫集合物件的成員函式。  例如：  
  
     [!code-cpp[NVC_MFCCollections#8](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_2.cpp)]  
  
3.  如果需要，請實作 [Helper 函式](../mfc/reference/collection-class-helpers.md) 和 [SerializeElements](../Topic/SerializeElements.md)。  如需實作這些函式的詳細資訊，請參閱 [實作 Helper 函式](#_core_implementing_helper_functions)。  
  
 這個範例顯示整數清單的宣告。  在步驟 1 中的第一個參數是做為清單項目中儲存的資料型別。  第二個參數的資料如何傳遞至和從集合類別的成員函式所傳回，例如 **Add** 和 `GetAt`。  
  
##  <a name="_core_implementing_helper_functions"></a> 實作協助函式  
 範本架構集合將 `CArray`、 `CList`和您可以自訂如需要針對衍生集合類別的 `CMap` 使用五個全域 Helper 函式。  如需這些 Helper 函式的詳細資訊，請參閱《 *MFC 參考》中的*[集合類別 Helper](../mfc/reference/collection-class-helpers.md) 。  序列化函式的實作需要的對樣板架構集合類別的大部分使用。  
  
###  <a name="_core_serializing_elements"></a> 序列化項目  
 `CArray`、 `CList`和 `CMap` 類別從封存呼叫 `SerializeElements` 儲存至集合項目或讀取它們。  
  
 `SerializeElements` 協助程式函式的預設實作會在物件上執行位元寫入封存，或者位元從封存讀取到物件，取決於是否儲存物件或從封存中擷取。  如果動作不是適當的，覆寫 `SerializeElements` 。  
  
 如果您的集合來儲存衍生自 `CObject` 的物件，而且想要在集合項目類別的實作使用 `IMPLEMENT_SERIAL` 巨集，您可以利用序列化功能內建在 `CArchive` 和 `CObject`:  
  
 [!code-cpp[NVC_MFCCollections#9](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_3.cpp)]  
  
 `CArchive` 的插入運算子呼叫 `CObject::Serialize` \(或該函式覆寫\) 每個 **CPerson** 物件的。  
  
##  <a name="_core_using_nontemplate_collection_classes"></a> 使用非樣板集合類別  
 MFC 也支援集合類別簡介使用 MFC 1.0 版。  這些類別不是以 MFC ODBC 類別為基礎。  它們可以用來包含支援的型別、 **UINT**`CObject*`、 `DWORD`和 `CString`資料。  您可以使用這些預先定義的集合 \(例如 `CObList`\) 保留從 `CObject`衍生的物件集合。  MFC 也提供預先定義的集合有基本型別 \(例如 **UINT** 和 null 指標 \(`void`\*\)。  不過，一般而言，定義自己的型別安全集合含有特定的類別和它的衍生的物件通常會很有幫助。  請注意使用樣板類別，這樣做會根據範本中的集合類別是比更多工作。  
  
 有兩種方式建立非樣板集合的型別安全集合:  
  
1.  在必要時使用有型別轉換的非範本集合。  這是最簡單的辦法。  
  
2.  衍生自並擴充非樣板型別安全集合。  
  
#### 用於型別轉換的非樣板集合  
  
1.  直接使用其中一個非範本類別，例如 `CWordArray`。  
  
     例如，您可以建立 `CWordArray` 並加入任何 32 位元值給它，然後擷取它們。  沒有任何項目。  您可以使用預先定義的功能。  
  
     您也可以使用預先定義的集合，例如 `CObList`，其包含所有衍生自 `CObject`的物件。  `CObList` 集合定義存放指標到 `CObject`。  當您從清單中擷取物件，您可能必須將結果轉換為適當的型別，因為 `CObList` 函式傳回 `CObject`的指標。  例如，在中，如果您在 `CObList` 集合中 `CPerson` 物件，您必須轉型為已擷取的項目是指標到 `CPerson` 物件。  下列範例會使用 `CObList` 集合中保留 `CPerson` 物件:  
  
     [!code-cpp[NVC_MFCCollections#10](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_4.cpp)]  
  
     這個技術視需要使用預先定義的集合型別和轉型可能已滿為您的許多集合需要。  如果您需要進一步功能或多個型別安全，請使用樣板類別或依照下一個程序。  
  
#### 衍生並擴充非範本型別安全集合。  
  
1.  從其中一個預先定義非範本類別衍生您自己的集合類別。  
  
     當您衍生您的類別時，您可以將型別安全包裝函式提供型別安全的介面給現有的函式。  
  
     例如，如果您，衍生自 `CObList` 的清單中保留 `CPerson` 物件，您可以將包裝函式 \( `AddHeadPerson` 和 `GetHeadPerson`，如下所示。  
  
     [!code-cpp[NVC_MFCCollections#11](../mfc/codesnippet/CPP/how-to-make-a-type-safe-collection_5.h)]  
  
     這些包裝函式提供型別安全方式從這個衍生的清單中加入和擷取 `CPerson` 物件。  您可以為 `GetHeadPerson` 函式，您封裝型別轉型。  
  
     您可以定義擴充功能集合而非包裝在型別安全包裝函式的現有功能的新函式也可以加入新的功能。  例如， [刪除在 CObject 集合的所有物件。](../mfc/deleting-all-objects-in-a-cobject-collection.md) 文章說明一個函式會刪除清單中的所有物件。  這個函式可以加入到衍生類別做為成員函式。  
  
## 請參閱  
 [集合](../mfc/collections.md)