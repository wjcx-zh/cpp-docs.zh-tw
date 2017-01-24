---
title: "IView Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IView class"
  - "views [MFC]"
  - "檢視, 類別"
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: 23
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IView Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行 [CWinFormsView](../../mfc/reference/cwinformsview-class.md) 使用檢視傳送告知給 Managed 控制項的方法。  
  
## 語法  
  
```  
interface class IView  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IView::OnActivateView](../Topic/IView::OnActivateView.md)|呼叫 MFC，在檢視中啟用或停用。|  
|[IView::OnInitialUpdate](../Topic/IView::OnInitialUpdate.md)|呼叫由架構，在這個檢視會先附加至文件之後，，但是，在檢視最初顯示。|  
|[IView::OnUpdate](../Topic/IView::OnUpdate.md)|呼叫 MFC 修改後，以檢視的資料;這個函式可以讓這個檢視會更新其顯示反映變更。|  
  
## 備註  
 `IView` 執行 `CWinFormsView` 使用轉送一般檢視通知至裝載 Managed 控制項的方法。  這些是 [OnInitialUpdate](../Topic/IView::OnInitialUpdate.md)、 [OnUpdate](../Topic/IView::OnUpdate.md) 和 [OnActivateView](../Topic/IView::OnActivateView.md)。  
  
 `IView` 類似， [CView](../../mfc/reference/cview-class.md)，但只能使用具有 Managed 檢視和控制項。  
  
 如需使用 Windows Form 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## 需求  
 標題:afxwinforms.h \(定義於組件\\ atlmfc \\ lib mfcmifc80.dll\)  
  
## 請參閱  
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)