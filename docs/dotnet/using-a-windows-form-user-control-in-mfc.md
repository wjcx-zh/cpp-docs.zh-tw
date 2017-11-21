---
title: "使用 Windows 表單在 MFC 中的使用者控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e836730942b3293ff8adc6aa7f8c75f4d2376cc1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>在 MFC 中使用 Windows Form 使用者控制項
使用 MFC Windows Form 支援類別，您可以裝載 Windows Form 控制項在 MFC 應用程式為 ActiveX 控制項，MFC 對話方塊或檢視內。 此外，Windows Form 表單可以裝載為 MFC 對話方塊。  
  
 下列章節說明如何：  
  
-   裝載 Windows Form 控制項在 MFC 對話方塊中。  
  
-   Windows Form 使用者控制項裝載為 MFC 檢視。  
  
-   因為 MFC 對話方塊中裝載 Windows Form 表單。  
  
> [!NOTE]
>  只有在使用 MFC 動態連結的專案中的 MFC Windows Form 整合運作 （AFXDLL 定義所在的專案）。  
  
> [!NOTE]
>  當您建置您的應用程式使用私用 （修改） 的 MFC Windows Form 介面 DLL (mfcmifc80.dll) 複本時，它將無法安裝在 GAC 中，除非 Microsoft 金鑰取代您自己的廠商金鑰。 如需有關簽署的組件的詳細資訊，請參閱[使用組件設計程式](/dotnet/framework/app-domains/programming-with-assemblies)和[強式名稱組件 （組件簽署） (C + + CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 使用 Windows Form 應用程式的範例，請參閱[BirthdayPicker 範例： 使用 Windows Form 示範.NET Framework 資源](http://msdn.microsoft.com/en-us/ac932aed-5502-4667-be29-709bca435317)，[計算機範例： Windows Form Pocket 計算機](http://msdn.microsoft.com/en-us/2283b516-3b7e-45f2-80c4-fdcfb366ce25)，和[Scribble 範例： MDI 繪圖應用程式](http://msdn.microsoft.com/en-us/f025da3e-659b-4222-b991-554a1b8b2358)。  
  
 顯示與 MFC 一起使用的 Windows Form 的範例應用程式，請參閱[MFC 和 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
 如果您的 MFC 應用程式使用 Windows Form，您需要重新發佈 mfcmifc90.dll 與您的應用程式。 如需詳細資訊，請參閱[轉散發 MFC 程式庫](../ide/redistributing-the-mfc-library.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [將 Windows Forms 使用者控制項裝載至 MFC 對話方塊中](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)  
  
 [將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)  
  
 [將 Windows Forms 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)  
  
## <a name="reference"></a>參考資料  
 [CWinFormsControl 類別](../mfc/reference/cwinformscontrol-class.md)  
  
 [CWinFormsDialog 類別](../mfc/reference/cwinformsdialog-class.md)  
  
 [CWinFormsView 類別](../mfc/reference/cwinformsview-class.md)  
  
 [ICommandSource 介面](../mfc/reference/icommandsource-interface.md)  
  
 [ICommandTarget 介面](../mfc/reference/icommandtarget-interface.md)  
  
 [ICommandUI 介面](../mfc/reference/icommandui-interface.md)  
  
 [IView 介面](../mfc/reference/iview-interface.md)  
  
 [CommandHandler](../atl/commandhandler.md)  
  
 [DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)  
  
 [UICheckState](../mfc/reference/uicheckstate-enumeration.md)  
  
## <a name="related-sections"></a>相關章節  
 [Windows Forms](/dotnet/framework/winforms/index)  
  
 [Windows Forms 控制項](/dotnet/framework/winforms/controls/index)  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [表單檢視](../mfc/form-views-mfc.md)