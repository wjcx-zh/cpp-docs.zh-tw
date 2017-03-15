---
title: "從 CObject 衍生類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 類別, 衍生自"
  - "CObject 類別, 衍生可序列化的類別"
  - "DECLARE_DYNAMIC 巨集"
  - "DECLARE_DYNCREATE 巨集"
  - "DECLARE_SERIAL 巨集"
  - "衍生類別, 來自 CObject"
  - "巨集 [C++], 序列化"
  - "序列化 [C++], 巨集"
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從 CObject 衍生類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明衍生自 [CObject](../mfc/reference/cobject-class.md)類別的最低需求步驟。  其他 `CObject` 類別文件說明採用指定 `CObject` 功能的優點所需的步驟，如序列化和診斷偵錯支援。  
  
 在 `CObject`的相關討論中，經常使用詞彙「介面檔案」及「實作檔」。  介面檔 \(通常稱為標頭檔或 .H 檔案\) 包含使用類別必要的類別宣告和任何其他資訊。  實作檔 \(或 .CPP 檔案\) 包含類別定義和實作類別成員函式的程式碼。  例如，針對名為 `CPerson` 的類別，您通常會建立名為 PERSON.H 介面檔案及名為 PERSON.CPP 的實作檔案。  不過，對於一些不在應用程式之間共用的小類別，合併介面和時做成一個單一的 .CPP 檔案有時會比較簡單。  
  
 當從 `CObject` 衍生類別時，您可以從功能的四層選取：  
  
-   基本功能：對直行接端費別資訊或序列化未支援，但不包括診斷記憶體管理。  
  
-   基本功能加上支援執行階段類別資訊。  
  
-   基本功能加上支援執行階段類別資訊和動態建立。  
  
-   基本功能加上支援執行階段類別資訊、動態建立和序列化。  
  
 類別設計為重複使用 \(以便稍後做為基底類別\) 應該至少包含執行階段類別支援和序列化支援，如果任何未來的序列化需求被期待。  
  
 您可以使用衍生自 `CObject` 類別的宣告和實作中的特定宣告和實作巨集，選取層級功能。  
  
 下表顯示用來支援序列化和執行階段資訊的巨集之間的關聯性。  
  
### 用來序列化和執行階段資訊的巨集  
  
|使用的巨集|CObject::IsKindOf|CRuntimeClass<br /><br /> CreateObject|CArchive::operator\>\><br /><br /> CArchive::operator\<\<|  
|-----------|-----------------------|------------------------------------|-------------------------------------------------------|  
|基礎 `CObject` 的功能。|沒有|沒有|沒有|  
|`DECLARE_DYNAMIC`|有|沒有|沒有|  
|`DECLARE_DYNCREATE`|有|有|沒有|  
|`DECLARE_SERIAL`|有|有|有|  
  
#### 使用基礎 CObject 功能  
  
1.  使用標準 C\+\+ 語法從 `CObject` 衍生您自己的類別 \(或從衍生自 `CObject`的類別\)。  
  
     下列範例顯示最簡單的情況下，衍生自 `CObject` 的類別：  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/CPP/deriving-a-class-from-cobject_1.h)]  
  
 不過，通常您可以覆寫一些 `CObject` 成員函式來處理您新類別的特性。  例如，您可能通常要覆寫 `CObject` 的 `Dump` 函式為您的類別內容提供偵錯輸出。  如需如何覆寫 `Dump`的詳細資料，請參閱本文件的 [診斷:傾印物件內容。](http://msdn.microsoft.com/zh-tw/727855b1-5a83-44bd-9fe3-f1d535584b59)。  您可能也要覆寫 `CObject` 的 `AssertValid` 函式提供自訂的測試驗證類別物件的資料成員的一致性。  如需描述如何覆寫 `AssertValid`，請參閱 [MFC ASSERT\_VALID 和 CObject::AssertValid](http://msdn.microsoft.com/zh-tw/7654fb75-9e9a-499a-8165-0a96faf2d5e6)。  
  
 [指定層級的功能](../mfc/specifying-levels-of-functionality.md) 文章說明如何指定其他層級功能，包括執行階段類別資訊、動態物件建立和序列化。  
  
## 請參閱  
 [使用 CObject](../mfc/using-cobject.md)