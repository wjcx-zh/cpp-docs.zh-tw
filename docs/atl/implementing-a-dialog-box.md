---
title: "Implementing a Dialog Box | Microsoft Docs"
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
  - "ATL, 對話方塊"
  - "CAxDialogImpl class, implementing dialog boxes in ATL"
  - "CSimpleDialog class, implementing dialog boxes in ATL"
  - "對話方塊, ATL"
ms.assetid: 478525f2-aa6a-435a-b162-68fc8aa98a8e
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有兩種方式可以將對話方塊加入至 ATL 專案:使用 ATL 對話方塊精靈或手動加入。  
  
## 加入 ATL 對話方塊精靈的對話方塊。  
 在 [加入類別對話方塊。](../ide/add-class-dialog-box.md)，選取 ATL 對話方塊物件將對話方塊加入至 ATL 專案。  填入 ATL 對話方塊精靈為適當並按一下 **完成**。  精靈會將 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) 從衍生的類別加入至專案。  開啟 \[**檢視**\] 從  功能表上的 \[資源檢視\] 中，找出您的對話方塊，然後按兩下以開啟 \[資源編輯器。  
  
> [!NOTE]
>  如果您的對話方塊 `CAxDialogImpl`從衍生自類別，它可以裝載 ActiveX 控制項和視窗。  如果您不想要額外負荷在您的對話方塊類別的 ActiveX 控制項支援，請使用 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 或 [CDialogImpl](../atl/reference/cdialogimpl-class.md) 。  
  
 訊息和事件處理常式可以加入至對話方塊類別從 \[類別檢視\]。  如需詳細資訊，請參閱[加入 ATL 訊息處理常式](../atl/adding-an-atl-message-handler.md)。  
  
## 手動加入對話方塊  
 實作對話方塊類似於實作視窗。  您從 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)、 [CDialogImpl](../atl/reference/cdialogimpl-class.md)或 [CSimpleDialog](../atl/reference/csimpledialog-class.md) 衍生類別並宣告 [訊息對應](../atl/message-maps-atl.md) 處理訊息。  不過，您可以在您的衍生類別也必須指定對話方塊樣板資源 ID。  您的類別必須有資料成員呼叫這個運算式值的 `IDD` 。  
  
> [!NOTE]
>  使用 ATL 對話方塊精靈時，當您建立對話方塊，則會自動將 `IDD` 成員做為 `enum` 型別。  
  
 `CDialogImpl` 可讓您實作該強制回應或非強制回應對話方塊主視窗控制項。  `CAxDialogImpl` 可讓您實作裝載 ActiveX 控制項和視窗的強制回應或非強制回應對話方塊。  
  
 若要建立強制回應對話方塊，請建立您自己的執行個體 `CDialogImpl`衍生的 \(或 `CAxDialogImpl`衍生\) 類別來呼叫 [DoModal](../Topic/CDialogImpl::DoModal.md) 方法。  若要關閉強制回應對話方塊，請呼叫從訊息處理常式的 [EndDialog](../Topic/CDialogImpl::EndDialog.md) 方法。  若要建立非強制回應對話方塊，請呼叫 [建立](../Topic/CDialogImpl::Create.md) 方法 \(而不是 `DoModal`。  若要終結非強制回應對話方塊，請呼叫 [DestroyWindow](../Topic/CDialogImpl::DestroyWindow.md)。  
  
 接收事件。 [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)自動呼叫。  實作對話方塊的訊息處理常式，您會 `CWindowImpl`之處理常式的衍生類別。  如果有特定訊息傳回值，請將它當做 `LRESULT`。  傳回的 `LRESULT` 值由適當處理 ATL 對應由 Windows 對話方塊處理常式。  如需詳細資訊，請為 atlwin.h 的 [CDialogImplBaseT::DialogProc](../Topic/CDialogImpl::DialogProc.md) 請參閱原始程式碼。  
  
## 範例  
 下列類別會實作一個對話方塊:  
  
 [!code-cpp[NVC_ATL_Windowing#66](../atl/codesnippet/CPP/implementing-a-dialog-box_1.h)]  
  
## 請參閱  
 [視窗類別](../atl/atl-window-classes.md)