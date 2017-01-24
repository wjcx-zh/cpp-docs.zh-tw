---
title: "宣告屬性視窗選取範圍追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK], 屬性頁支援"
  - "屬性頁, 追蹤選取範圍"
  - "屬性視窗, 追蹤選取範圍"
  - "選取範圍, 追蹤"
  - "編輯器 [Visual Studio SDK], 屬性視窗支援"
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 宣告屬性視窗選取範圍追蹤
如果您想要使用的**屬性** \] 視窗或 **屬性**頁面，例如表單、 文字或選取您想要查看屬性，則必須有完整了解如何在您調整選取範圍。  例如，您必須知道您是否有限制單選或複選。  然後，您需要通知您的選取項目類型 \(單一或多個\) 到 IDE 時使用<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面。  這個介面會提供所需的資訊**屬性**視窗。  
  
### 若要宣告環境的選取範圍  
  
1.  Call `QueryInterface` for <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>.  
  
    1.  若要這樣做，請使用站台指標傳遞至檢視中，建立時。  
  
    2.  呼叫`QueryService`的檢視從`SID_STrackSelection`服務。  
  
         此舉會讓變數的指標， <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>。  
  
2.  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>方法，每當您的選取範圍變更，並傳遞指標至物件實作<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>。  
  
     選取的容器物件可以使用單一或多重選取，並包含選取項目的資訊，在`IDispatch`物件。  呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>方法會告知**屬性**的選取範圍已變更的視窗。  **屬性**視窗然後會使用這些物件在<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>來判斷是否已發生一個或多個選取的項目，以及是否有實際物件的選取項目。  
  
     如果您指定一個多重指定範圍，然後在**屬性**視窗尋找通用的屬性之物件的交集。  如果您指定一個物件的選取範圍，然後在**屬性** \] 視窗會顯示所有的一個物件的屬性。  
  
## 請參閱  
 [擴充屬性](../Topic/Extending%20Properties.md)   
 [屬性頁](../Topic/Property%20Pages.md)