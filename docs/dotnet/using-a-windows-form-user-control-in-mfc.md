---
title: "在 MFC 中使用 Windows Form 使用者控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "MFC [c + +]，Windows Form 支援"
  - "互通性 [c + +]，在 MFC 中的 Windows Form"
  - "互通性 [c + +] MFC"
  - "interop [c + +]，在 MFC 中的 Windows Form"
  - "interop [c + +] MFC"
  - "Windows Form [c + +]，MFC 支援"
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 MFC 中使用 Windows Form 使用者控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 MFC Windows Form 支援類別，您可以裝載 Windows Form 控制項在 MFC 應用程式為 MFC 對話方塊或檢視表中的 ActiveX 控制項。 此外，Windows Form 表單可以裝載為 MFC 對話方塊。  
  
 下列章節說明如何︰  
  
-   裝載 Windows Form 控制項在 MFC 對話方塊中。  
  
-   將 Windows Form 使用者控制項裝載為 MFC 檢視。  
  
-   因為 MFC 對話方塊中裝載 Windows Form 表單。  
  
> [!NOTE]
>  MFC Windows Form 整合只能在動態連結與 MFC 專案中的工作 （AFXDLL 定義所在的專案）。  
  
> [!NOTE]
>  當您建置應用程式使用 MFC Windows Form 介面 DLL (mfcmifc80.dll) 的私用 （已修改） 複本時，它將無法安裝到 GAC 中，除非您使用您自己的廠商金鑰來取代 Microsoft 金鑰。 如需有關簽署的組件的詳細資訊，請參閱 [使用組件設計程式](../Topic/Programming%20with%20Assemblies.md) 和 [強式名稱組件 （組件簽署） (C + + /cli CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 使用 Windows Form 應用程式的範例，請參閱 [BirthdayPicker 範例︰ 使用 Windows Form 示範.NET Framework 資源](http://msdn.microsoft.com/zh-tw/ac932aed-5502-4667-be29-709bca435317), ，[計算機範例︰ Windows Form 的袖珍計算機](http://msdn.microsoft.com/zh-tw/2283b516-3b7e-45f2-80c4-fdcfb366ce25), ，和 [Scribble 範例︰ MDI 繪圖應用程式](http://msdn.microsoft.com/zh-tw/f025da3e-659b-4222-b991-554a1b8b2358)。  
  
 顯示與 MFC 一起使用的 Windows Form 範例應用程式，請參閱 [MFC 和 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
 如果您的 MFC 應用程式使用 Windows Form，您需要重新發佈您的應用程式的 mfcmifc90.dll。 如需詳細資訊，請參閱 [轉散發 MFC 程式庫](../ide/redistributing-the-mfc-library.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [MFC 對話方塊中的 Windows Form 使用者控制項裝載](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)  
  
 [Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)  
  
 [Windows Form 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)  
  
## <a name="reference"></a>參考資料  
 [CWinFormsControl 類別](../mfc/reference/cwinformscontrol-class.md)  
  
 [CWinFormsDialog 類別](../mfc/reference/cwinformsdialog-class.md)  
  
 [CWinFormsView 類別](../mfc/reference/cwinformsview-class.md)  
  
 [ICommandSource 介面](../mfc/reference/icommandsource-interface.md)  
  
 [ICommandTarget 介面](../mfc/reference/icommandtarget-interface.md)  
  
 [ICommandUI 介面](../mfc/reference/icommandui-interface.md)  
  
 [IView 介面](../mfc/reference/iview-interface.md)  
  
 [CommandHandler](../Topic/CommandHandler%20Delegate.md)  
  
 [CommandUIHandler](../Topic/CommandUIHandler%20Delegate.md)  
  
 [DDX_ManagedControl](../Topic/DDX_ManagedControl.md)  
  
 [UICheckState](../Topic/UICheckState%20Enumeration.md)  
  
## <a name="related-sections"></a>相關章節  
 [Windows Form](../Topic/Windows%20Forms.md)  
  
 [Windows Form 控制項](../Topic/Windows%20Forms%20Controls.md)  
  
 [ASP.NET 使用者控制項](../Topic/ASP.NET%20User%20Controls.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [表單檢視](../mfc/form-views-mfc.md)