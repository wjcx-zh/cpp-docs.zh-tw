---
title: "存取執行階段類別資訊 | Microsoft Docs"
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
helpviewer_keywords: 
  - "類別 [C++], 執行階段類別資訊"
  - "CObject 類別, 存取執行階段類別資訊"
  - "CObject 類別, 與 RTTI"
  - "CObject 類別, 使用 IsKindOf 方法"
  - "CObject 類別, 使用 RUNTIME_CLASS 巨集"
  - "IsKindOf 方法"
  - "RTTI 編譯器選項"
  - "執行階段"
  - "執行階段, 類別資訊"
  - "執行階段類別"
  - "執行階段類別, 存取資訊"
  - "RUNTIME_CLASS 巨集"
  - "RUNTIME_CLASS 巨集, 使用"
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 存取執行階段類別資訊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何在執行階段存取物件之類別的資訊。  
  
> [!NOTE]
>  MFC 在 Visual C\+\+ 4.0 不使用 [執行階段型別資訊](../cpp/run-time-type-information.md) \(RTTI\) 支援。  
  
 如果您從 [CObject](../mfc/reference/cobject-class.md) 衍生您的類別，並使用 從 [CObject衍生類別](../mfc/deriving-a-class-from-cobject.md) 一文所述的 **DECLARE**\_**DYNAMIC** 和 `IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE`，或 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 巨集，`CObject` 類別將有能力可以在執行階段判斷物件的實際類別。  
  
 當函式引數的額外型別檢查是必要時，以及當您必須根據物件的類別撰寫特殊功能的程式碼時，這項功能十分實用。  不過，通常不建議使用這種作法，因為這會重複虛擬函式的功能。  
  
 `CObject` 成員函式 `IsKindOf` 可以用來判斷特定物件是否屬於指定的類別，或是否衍生自特定類別。  對 `IsKindOf` 的引數是 `CRuntimeClass` 物件，您可以以類別名稱使用 `RUNTIME_CLASS` 巨集來取得。  
  
### 若要使用 RUNTIME\_CLASS 巨集  
  
1.  與類別名稱使用 `RUNTIME_CLASS` ，如下所示為 `CObject` 類別：  
  
     [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/CPP/accessing-run-time-class-information_1.cpp)]  
  
 您很少需要直接存取執行階段類別的物件。  一般用法是傳遞執行階段類別物件至 `IsKindOf` 函式，如下面的程序所示。  `IsKindOf` 函式會測試可視物件是否屬於特定類別。  
  
#### 若要使用 IsKindOf 函式  
  
1.  請確定類別擁有執行階段類別支援。  也就是，類別必須是直接或間接地衍生自 `CObject` 並且使用 [從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md) 一文所述的 **DECLARE**\_**DYNAMIC** 和 `IMPLEMENT_DYNAMIC`， `DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE`，或 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 巨集。  
  
2.  呼叫該類別之物件的 `IsKindOf` 成員函式，使用 `RUNTIME_CLASS` 巨集產生 `CRuntimeClass` 引數，如下所示：  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/CPP/accessing-run-time-class-information_2.h)]  
  
     [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/CPP/accessing-run-time-class-information_3.cpp)]  
  
    > [!NOTE]
    >  如果物件是指定類別的成員或是衍生自特定的類別之類別，則 IsKindOf 傳回 **TRUE** 。  `IsKindOf` 不支援多重繼承或虛擬基底類別 \(Base Class\)，不過您可以為衍生的 Microsoft Foundation Class 在必要時，使用多重繼承。  
  
 執行階段類別資訊的一個用法是物件的動態建立。  這個流程在這篇文章 [動態物件建立](../mfc/dynamic-object-creation.md) 中已討論。  
  
 如需序列化和執行階段類別資訊的詳細資訊，請參閱文件 [MFC 中的檔案](../mfc/files-in-mfc.md) 和 [序列化](../mfc/serialization-in-mfc.md)。  
  
## 請參閱  
 [使用 CObject](../mfc/using-cobject.md)