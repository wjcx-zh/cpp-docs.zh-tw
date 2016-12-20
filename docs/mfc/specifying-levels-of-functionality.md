---
title: "指定功能層級 | Microsoft Docs"
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
  - "CObject 類別, 將功能加入至衍生類別"
  - "動態建立支援"
  - "層級 [C++]"
  - "層級 [C++], CObject 中的功能"
  - "執行階段 [C++], 類別資訊"
  - "執行階段類別, 資訊支援"
  - "序列化 [C++], Cobject"
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 指定功能層級
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何加入下列層級功能加入至 [CObject](../mfc/reference/cobject-class.md)衍生類別:  
  
-   [執行階段類別資訊](#_core_to_add_run.2d.time_class_information)  
  
-   [動態建立支援](#_core_to_add_dynamic_creation_support)  
  
-   [序列化支援。](#_core_to_add_serialization_support)  
  
 如需 `CObject` 功能的一般說明，請參閱本文件的 [從衍生類別 CObject](../mfc/deriving-a-class-from-cobject.md)。  
  
#### 將執行階段類別資訊  
  
1.  從 `CObject`衍生您自己的類別，如 [從衍生類別 CObject](../mfc/deriving-a-class-from-cobject.md) 文件中所述。  
  
2.  使用 `DECLARE_DYNAMIC` 巨集在類別宣告，如下所示:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/CPP/specifying-levels-of-functionality_1.h)]  
  
3.  使用 `IMPLEMENT_DYNAMIC` 巨集在實作檔 \(.CPP\) 的類別。  這個巨集以做為引數類別和其基底類別的名稱，如下所示:  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/CPP/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  永遠在實作檔 \(.CPP\) 的放置 `IMPLEMENT_DYNAMIC` 您的類別中。  應該一次只能在編譯期間評估 `IMPLEMENT_DYNAMIC` 巨集也不應該使用介面檔 \(。在多個檔案可能會包含的 H\)。  
  
#### 將動態建立支援  
  
1.  從 `CObject` 衍生您的類別。  
  
2.  使用 `DECLARE_DYNCREATE` 巨集在類別宣告。  
  
3.  定義建構函式是不接收任何引數的建構函式\(預設建構函式\)。  
  
4.  使用 `IMPLEMENT_DYNCREATE` 類別實作檔中的巨集。  
  
#### 若要加入序列化支援  
  
1.  從 `CObject` 衍生您的類別。  
  
2.  覆寫 `Serialize` 成員函式。  
  
    > [!NOTE]
    >  也就是說，如果您直接呼叫 `Serialize` 您不想將多型指標序列化物件，略過步驟 3 到步驟 5. 步驟。  
  
3.  使用 `DECLARE_SERIAL` 巨集在類別宣告。  
  
4.  定義建構函式是不接收任何引數的建構函式\(預設建構函式\)。  
  
5.  使用 `IMPLEMENT_SERIAL` 類別實作檔中的巨集。  
  
> [!NOTE]
>  對類別 \(稱為物件的「多型指標」按它 A\) 或是從 A 的任何衍生類別物件 \(假設， B\)。  透過多型指標要序列化，架構必須判斷序列化 \(b\) 物件的執行階段類別，，因為它可以是從某些基底類別衍生的任何類別物件 \(\)。  
  
 如需更詳細的資訊是關於如何啟用序列化，請從 `CObject`衍生您自己的類別，請參閱文件 [MFC 中的檔案](../mfc/files-in-mfc.md) 和 [序列化](../mfc/serialization-in-mfc.md)。  
  
## 請參閱  
 [從 CObject 衍生類別](../mfc/deriving-a-class-from-cobject.md)