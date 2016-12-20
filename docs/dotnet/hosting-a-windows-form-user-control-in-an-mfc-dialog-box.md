---
title: "將 Windows Form 使用者控制項裝載至 MFC 對話方塊中 | Microsoft Docs"
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
  - "裝載 Windows Form 控制項 [C++]"
  - "MFC [C++], Windows Form 支援"
  - "Windows Form [C++], MFC 支援"
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將 Windows Form 使用者控制項裝載至 MFC 對話方塊中
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 將 Windows Form 控制項裝載為特殊種類的 ActiveX 控制項，並使用 ActiveX 介面以及 <xref:System.Windows.Forms.Control> 類別的屬性和方法與控制項溝通。  建議您應該使用 .NET Framework 屬性和方法在控制項中操作。  
  
 如需示範 Windows Form 搭配 MFC 使用的範例應用程式，請參閱 [MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en) \(英文\)。  
  
> [!NOTE]
>  在目前的版本中，`CDialogBar`  物件無法裝載 Windows Form 控制項。  
  
## 在本節中  
 [如何：建立使用者控制項並裝載至對話方塊中](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)  
  
 [如何：使用 Windows Form 執行 DDX\/DDV 資料繫結](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)  
  
 [如何：從原生 C\+\+ 類別接收 Windows Form 事件](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)  
  
## 參考  
 [CWinFormsControl Class](../mfc/reference/cwinformscontrol-class.md) &#124; [CDialog Class](../mfc/reference/cdialog-class.md) &#124; [CWnd 類別](../mfc/reference/cwnd-class.md) &#124; <xref:System.Windows.Forms.Control>  
  
## 請參閱  
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows Form\/MFC 程式設計的差異](../dotnet/windows-forms-mfc-programming-differences.md)   
 [將 Windows Form 使用者控制項裝載為 MFC 檢視](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)   
 [將 Windows Form 使用者控制項裝載成 MFC 對話方塊](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)