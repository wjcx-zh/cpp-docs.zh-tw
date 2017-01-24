---
title: "透過封存儲存及載入 CObjects | Microsoft Docs"
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
  - "CArchive 類別, 儲存及載入物件"
  - "CObject 類別, CArchive 物件"
  - "CObjects"
  - "CObjects, 透過封存載入"
  - "Serialize 方法, 和 CArchive 運算子比較"
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 透過封存儲存及載入 CObjects
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

藉由封存儲存和載入 `CObject` 需要額外的考量。  在一些情況下，您應該呼叫物件的 `Serialize` 函式， `CArchive` 物件是 `Serialize` 呼叫的參數，與使用 `CArchive`的 **\<\<** 或 **\>\>** 運算子相反。  要注意的重要事情是 `CArchive` **\>\>** 運算子於記憶體建構 `CRuntimeClass` 會根據先前寫入檔案所儲存的封存的 `CObject` 資訊。  
  
 因此，您使用的是 `CArchive`，**\<\<** 與 **\>\>** 運算子，或呼叫 `Serialize`，會視 *需要* 載入封存動態地重建根據先前儲存的 `CRuntimeClass` 資訊的物件。  於下列案例使用 `Serialize` 函式：  
  
-   當還原序列化物件時，您事先知道物件的實際類別。  
  
-   當還原序列化物件時，您已經為其配置記憶體。  
  
> [!CAUTION]
>  如果您使用 `Serialize` 函式載入物件，您也必須使用 `Serialize` 函式儲存物件。  請勿使用 `CArchive` **\<\<** 運算子接著使用 `Serialize` 函式載入，或使用 `Serialize` 函式儲存接著使用 **CArchive \>\>** 運算子載入。  
  
 下面範例會說明此案例。  
  
 [!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/CPP/storing-and-loading-cobjects-via-an-archive_1.h)]  
  
 [!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/CPP/storing-and-loading-cobjects-via-an-archive_2.cpp)]  
  
 總而言之，因此，如果您的可序列化類別定義內嵌 **CObject** 為成員，您 *不* 應該為該物件使用 `CArchive` **\<\<** 和 **\>\>** 運算子，而是應該呼叫 `Serialize` 函式。  此外，如果您的可序列化類別定義了指標至 `CObject` \(或衍生自 `CObject`的物件\) 的成員，但是在它的建構函式建構這個其他物件，則也應該呼叫 `Serialize`。  
  
## 請參閱  
 [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)