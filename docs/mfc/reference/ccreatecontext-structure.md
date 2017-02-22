---
title: "CCreateContext Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCreateContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCreateContext structure"
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CCreateContext Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

架構會使用 `CCreateContext` 結構時，它會建立與文件的框架視窗和檢視時。  
  
## 語法  
  
```  
struct CCreateContext  
```  
  
## 備註  
 `CCreateContext` 是結構，而且沒有基底類別。  
  
 當您建立視窗時，這個結構的值會提供資訊的線上文件的元件加入至它的資料檢視。  如果您覆寫，建立程序的一部分，您只需要使用 `CCreateContext` 。  
  
 `CCreateContext` 結構包含指標、文件框架視窗、檢視和文件樣板。  它也包含識別檢視類型建立的指標 `CRuntimeClass` 。  執行階段類別資訊和目前資料指標是用來以動態方式建立新的檢視。  下表建議的方式和時機可能會使用每個 `CCreateContext` 成員:  
  
|成員|型別|什麼是。|  
|--------|--------|----------|  
|`m_pNewViewClass`|`CRuntimeClass*`|建立的新檢視的`CRuntimeClass` 。|  
|`m_pCurrentDoc`|`CDocument*`|與關聯的現有文件和新的檢視。|  
|`m_pNewDocTemplate`|`CDocTemplate*`|文件樣板與新的主框架視窗的建立。|  
|`m_pLastView`|`CView*`|其他檢視為模型的檢視，以分隔視窗檢視的建立或第二個檢視以文件中的。|  
|`m_pCurrentFrame`|`CFrameWnd*`|其他框架視窗的設計的框架視窗，在第二個框架視窗的建立文件中的。|  
  
 當文件範本建立文件和其相關的元件時，它會驗證在 `CCreateContext` 結構中儲存的資訊。  例如，不應用於一個不存在的資料建立檢視。  
  
> [!NOTE]
>  所有在 `CCreateContext` 的指標是選擇性的，而且可以是 `NULL` ，如果未指定或未知。  
  
 以下列出的函式「請參閱成員使用`CCreateContext` 」。如果您想要覆寫這些屬性，請參閱這些函式的說明特定的資訊。  
  
 這個的一般方針:  
  
-   當傳遞，因為視窗建立的引數，在 `CWnd::Create`， `CFrameWnd::Create`和 `CFrameWnd::LoadFrame`，建立指定之的內容應該連接的新視窗。  對於大部分的視窗，整個結構是選擇性的，而且 `NULL` 指標可傳遞至。  
  
-   對於可覆寫的成員函式，例如 `CFrameWnd::OnCreateClient`， `CCreateContext` 引數是選擇性的。  
  
-   檢視建立相關的成員函式，您必須提供足夠的資訊來建立檢視。  例如，在分割視窗中第一個檢視，您必須提供檢視類別資訊和目前的文件。  
  
 一般而言，如果您使用，此架構會預設值為，因此您可以忽略 `CCreateContext`。  如果您嘗試在進階的修改， MFC 程式庫原始程式碼或範例程式，例如， VIEWEX 會引導您。  如果您忘記必要參數，架構判斷提示會呼叫您要忘記。  
  
 如需 `CCreateContext`的相關資訊，請參閱 MFC 範例 [VIEWEX](../../top/visual-cpp-samples.md)。  
  
## 需求  
 **標題:** afxext.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../Topic/CFrameWnd::Create.md)   
 [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md)   
 [CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md)   
 [CSplitterWnd::Create](../Topic/CSplitterWnd::Create.md)   
 [CSplitterWnd::CreateView](../Topic/CSplitterWnd::CreateView.md)   
 [CWnd::Create](../Topic/CWnd::Create.md)