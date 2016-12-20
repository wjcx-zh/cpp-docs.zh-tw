---
title: "Understanding Window Traits | Microsoft Docs"
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
  - "window traits"
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Understanding Window Traits
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

視窗特性類別提供標準化用於 ATL 視窗物件建立的樣式提供簡單的方法。  視窗特性接受當做樣板參數。 [CWindowImpl](../atl/reference/cwindowimpl-class.md) 和其他 ATL 視窗類別做為提供在類別層級的預設視窗樣式模式。  
  
 如果視窗執行個體的建立者在呼叫明確提供樣式提供 [建立](../Topic/CWindowImpl::Create.md)特性，您可以使用類別來確保視窗仍會以正確的樣式。  您甚至可以確保特定模式為該視窗類別所有執行個體設定屬性，以允許其他樣式設定是以個別執行個體資料。  
  
## ATL 視窗特性範本  
 ATL 提供使用它們的樣板參數，可讓您設定預設樣式在編譯時期的兩個視窗特性範本。  
  
|類別|描述|  
|--------|--------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|請使用這個範本，當您想要提供所要使用的預設視窗樣式時，只有在其他模式在 \[ **建立**時的呼叫未指定。  樣式在執行階段提供優先於樣式設定可以在編譯時期。|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|請使用這個類別時，您要指定必須為 Windows 類別所設定的樣式時。  模式可在執行階段與樣式位元設定在編譯時期使用或運算子。|  
  
 除了這些範本之外， ATL 的視窗樣式的常用的組合提供 `CWinTraits` 範本有許多預先定義的特製化。  請參閱 [CWinTraits](../atl/reference/cwintraits-class.md) 參考文件取得完整詳細資料。  
  
## 自訂視窗特性  
 在特製化 ATL 提供的其中一個範本不足，而您需要建立自己的特性類別的較不常見的情況下，您必須建立類別實作兩個靜態函式: `GetWndStyle` 和 **GetWndStyleEx**:  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/CPP/understanding-window-traits_1.h)]  
  
 這些函式。會透過它可以使用產生的樣式值的執行階段模式陣列值。  如果您的視窗特性類別當做 ATL 視窗類別的樣板引數，樣式值傳遞到這些靜態函式將會傳遞做為樣式引數傳遞至 [建立](../Topic/CWindowImpl::Create.md)。  
  
## 請參閱  
 [視窗類別](../atl/atl-window-classes.md)