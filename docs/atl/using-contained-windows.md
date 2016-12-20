---
title: "Using Contained Windows | Microsoft Docs"
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
  - "ATL, 視窗"
  - "contained windows in ATL"
  - "windows [C++], ATL"
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using Contained Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 實作包含了 [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)的視窗。  所包含的視窗表示委派其訊息為容器物件而不是處理它們在其類別的視窗。  
  
> [!NOTE]
>  您不需要從 `CContainedWindowT` 衍生類別才能使用所包含的視窗。  
  
 使用所包含的視窗，您可以在的 Superclass 現有 Windows 分類或子類別現有視窗。  若要建立類別的 Superclass 現有視窗中的  視窗中，請先指定現有類別名稱在建構函式 \(Constructor\) `CContainedWindowT` 物件。  然後呼叫 `CContainedWindowT::Create`。  若要子類別化現有的視窗中，您不需要指定視窗類別名稱 \(如建構函式中傳遞 **NULL** \)。  請改為使用控制代碼的 `CContainedWindowT::SubclassWindow` 方法加入子類別化的視窗。  
  
 在容器的資料成員分類，您通常會使用所包含的視窗。  容器不需要是視窗;然而，它必須從 [CMessageMap](../atl/reference/cmessagemap-class.md)衍生。  
  
 所包含的視窗可以使用替代的訊息對應的處理會自己的訊息。  如果您有多個被收納的視窗，您應該宣告數個替代的訊息對應，每次都使用不同的內含視窗對應。  
  
## 範例  
 下列容器類別的範例有兩個內含視窗中:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/CPP/using-contained-windows_1.h)]  
  
 如需從內容之視窗的詳細資訊，請參閱 [SUBEDIT](../top/visual-cpp-samples.md) 範例。  
  
## 請參閱  
 [視窗類別](../atl/atl-window-classes.md)