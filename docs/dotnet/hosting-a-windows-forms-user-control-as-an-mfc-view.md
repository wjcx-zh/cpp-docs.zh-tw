---
title: "將 Windows Form 使用者控制項裝載為 MFC 檢視 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Windows Form 控制項 [C++], 裝載為 MFC 檢視"
ms.assetid: 43c02ab4-1366-434c-a980-0b19326d6ea0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將 Windows Form 使用者控制項裝載為 MFC 檢視
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 使用 CWinFormsView 類別來裝載 \(Host\) MFC 檢視中的 Windows Form 使用者控制項。  MFC Windows Form 檢視是 ActiveX 控制項。  使用者控制項是裝載為原生 \(Native\) 檢視的子系，並佔用原生檢視的整個工作區 \(Client Area\)。  
  
 結果類似 [CFormView Class](../mfc/reference/cformview-class.md)所使用的模型。  可以讓您利用 Windows Form 設計工具和執行階段來建立豐富的表單架構檢視。  
  
 因為 MFC Windows Form 檢視是 ActiveX 控制項，所以和 MFC 檢視擁有不同的 `hwnd`。  他們也不能做為 [CView](../mfc/reference/cview-class.md) 檢視的指標來傳遞。  一般而言，會使用 .NET Framework 方法和 Windows Form 檢視搭配使用，很少使用 Win32。  
  
 如需示範 Windows Form 搭配 MFC 使用的範例應用程式，請參閱 [MFC 與 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en) \(英文\)。  
  
## 在本節中  
 [如何：建立使用者控制項並裝載 MDI 檢視](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)  
  
 [如何：新增命令傳送至 Windows Form 控制項](../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)  
  
 [如何：呼叫 Windows Form 控制項的屬性和方法](../dotnet/how-to-call-properties-and-methods-of-the-windows-forms-control.md)  
  
## 請參閱  
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [如何：撰寫複合控制項](../Topic/How%20to:%20Author%20Composite%20Controls.md)